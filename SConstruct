env = Environment(
    tools=['pdflatex', 'pdftex', 'tex'],
    )

env.AppendUnique(PDFLATEXFLAGS='--synctex=1')

if env.GetOption('silent'):
    env.AppendUnique(
        PDFLATEXFLAGS=['-file-line-error', '-interaction=batchmode'],
        BIBTEXFLAGS='-terse',
        )

env.PrependENVPath('PATH', [
        '/s/texlive-2011/bin',
        '/s/texlive-2010/bin',
        ])

pdf = env.PDF('rs.tex')[0]
Default(pdf)
Clean(pdf, pdf.target_from_source('', '.synctex.gz'))

ps = env.Command('main.ps', pdf, 'pdftops $SOURCE $TARGET')

Depends(pdf, [
        'rs.bib',
        'plainyr-rev.bst',
        ])


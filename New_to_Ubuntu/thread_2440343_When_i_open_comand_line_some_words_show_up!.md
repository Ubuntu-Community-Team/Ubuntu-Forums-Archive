---
title: "When i open comand line some words show up!"
date: 2020-04-09
forum: New to Ubuntu
---

### Post by arditprenga on 2020-04-09
bash: /home/ardit/.bashrc: line 171: syntax error near unexpected token `PATH="$PATH:/opt/mssql-tools/bin"'
bash: /home/ardit/.bashrc: line 171: `esacexport PATH="$PATH:/opt/mssql-tools/bin"'


Any idea how to remove them :lolflag:

---

### Post by Impavidus on 2020-04-09
There's a syntax error in your .bashrc file, a hidden file used to initialise your shell. I'd expect the word "esac" to be somewhere on a line of its own and the line to append something to the PATH should start with "export", so I think you somehow lost a linebreak between those. You can edit the file with your favourite text editor.

---


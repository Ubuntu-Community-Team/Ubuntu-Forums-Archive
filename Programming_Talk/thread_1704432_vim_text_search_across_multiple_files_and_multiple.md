---
title: "vim text search across multiple files and multiple folders"
date: 2011-03-10
forum: Programming Talk
---

### Post by cybo on 2011-03-10
i'm working on a large project. the code is distributed across multiple directories and multiple files. i need to perform a text search very often in all of the project files. does anybody know if there is a way to do that in vim?

any help is appreciated.

---

### Post by DaithiF on 2011-03-10
[LEFT]I am a vim user but I do this kind of thing outside of vim (or within vim by calling out to an external command with :!somecommand)
[/LEFT]

For small-ish projects I have a per-project find+grep script, so for project abc i would have a script abcgrep on my path that i would call like:
abcgrep search_term1 [searchterm2] [etc...] 
which would output hits to stdout and optionally (with a -s parameter) also save results into a file for later inspection.

an example of such a script:
```
#!/bin/bash
rootdir=~/Projects/abc
outputdir=~/tmp/abcgrep

[[ $# -eq 0 ]] && { echo "abcgrep [-s] searchterm1 searchterm2"; echo " (-s = save results)"; exit 
0; }

[[ ! -d $outputdir ]] && mkdir $outputdir

if [[ $1 == "-s" ]]; then
    shift
    save_results=1
fi

cd $rootdir

[[ $? -ne 0 ]] && { echo "Failed to change dir to $rootdir, exiting"; exit 1;}

for term in $*
do
    echo "$term --> $(date)" | tee $outputdir/$term.out
    find . -path '*/.svn/*' -prune -o -path './dbdumps/*' -prune -o -exec grep -li $term {} \; | tee 
-a $outputdir/$term.out
    [[ $save_results -ne 1 ]] && rm -f $outputdir/$term.out
done

echo
echo "all done"
[[ $save_results -eq 1 ]] && echo "results saved in $outputdir"

```
note the find command has options for excluding certain directories ... a copule of examples in the one above would exclude subversion version control dirs and a directory containing database dump files (just an example)

For larger projects where a find + grep would take longer than the 30seconds or whatever your patience threshold might be, another option would be to look into an indexed search tool -- plenty of options available if you google it.

---

### Post by MadCow108 on 2011-03-10
[http://cscope.sourceforge.net/cscope_vim_tutorial.html](http://cscope.sourceforge.net/cscope_vim_tutorial.html)

---

### Post by cybo on 2011-03-14
thanks for the help everybody.

---


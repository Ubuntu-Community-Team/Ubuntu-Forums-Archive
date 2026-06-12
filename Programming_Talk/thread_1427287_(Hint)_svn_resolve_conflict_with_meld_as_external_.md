---
title: "(Hint) svn resolve conflict with meld as external tool"
date: 2010-03-11
forum: Programming Talk
---

### Post by sdaau on 2010-03-11
Hi all, 

Since I always forget about the procedure on what to do when experiencing an svn conflict - and additionally, how to employ an external tool like meld to do the diff; I finally made me a "reminder" interactive script what creates a repo and causes a conflict, and guides you through the resolution. Here the conflict will be resolved during the 'svn update' stage. 

First of all, in order to use meld as a tool during the 'svn update' stage, one needs a wrapper script for it:
```

touch ~/meldwrap.sh
chmod +x ~/meldwrap.sh
gedit  ~/meldwrap.sh

```And paste in the script below: 
```

#!/bin/sh

# if you simply want to see what command arguments are passed by subversion,
# simply uncomment following line, and comment rest of the script:
# echo "$@"

# http://pida.co.uk/wiki/UsingExternalDiffTools

# Configure your favorite diff program here.
DIFF="/usr/bin/meld"

# Subversion provides the paths we need as the sixth and seventh
# parameters.
LEFT=${3} # 'MINE' - was 6
RIGHT=${2} # 'THEIRS' (online) - was 7

# Call the diff command (change the following line to make sense for
# your merge program).
$DIFF $LEFT $RIGHT

# Return an errorcode of 0 if no differences were detected, 1 if some were.
# Any other errorcode will be treated as fatal.

```Note that the arguments are not the same as in the original script from [http://pida.co.uk/wiki/UsingExternalDiffTools](http://pida.co.uk/wiki/UsingExternalDiffTools) . 

Then, create a new script wherever you want, calling it 'svn-conflict-external.sh', and paste in the code below:
```

#!/usr/bin/env bash

# color chars
CSA=$(echo -e "\033[0;31m")
CSB=$(echo -e "\033[0;32m")
CSC=$(echo -e "\033[0;33m")
CE=$(echo -e "\033[0m")

# original dir
ODIR=$(pwd)

# external tool to resolve conflicts - chould have full path
EXTTOOL="~/meldwrap.sh"

function echoPause()
{
# function arguments are $1 etc..
echo "$1"
echo -n "${CSC}Press Enter to continue..${CE}"
read
echo
}

echoPause "svn-conflict-external.sh
simulate svn conflict interactively, by creating a local repo and tests
in dir: ${CSB}${ODIR}${CE}"

echo -n "Enter desired repo name and press [ENTER]: "
read reponame
echo

cmd="svnadmin create ${reponame}"
echoPause "Got repo name ${reponame}... About to run:
$CSA$cmd$CE"

$cmd


LCOPY1="${reponame}-1"
LCOPY2="${reponame}-2"
TFILE="aTextFile.txt"

cmd="svn co file://${ODIR}/${reponame} ${LCOPY1}"

echoPause "Created repo ${reponame}.
About to check out local copy for user 1 with
$CSA$cmd$CE"

$cmd

cmd1="cd ${LCOPY1}"
cmd2="echo \"Starting content\" > $TFILE"
cmd3="svn add $TFILE"
cmd4="svn ci -m \"Initial content\""
cmd5="cd .."

echoPause "Populating and comitting local copy for user 1 with initial content with:
$CSA$cmd1
$cmd2
$cmd3
$cmd4
$cmd5$CE"

# use eval wherever there are quotes in string:
$cmd1
pwd
eval $cmd2
$cmd3
eval $cmd4
$cmd5


cmd="svn co file://${ODIR}/${reponame} ${LCOPY2}"

echoPause "
Done. Checking out rev.1 for user 2 (though we could have just done 'cp -a ${LCOPY1} ${LCOPY2}'); about to run:
$CSA$cmd$CE"

$cmd

cmd1="cd ${LCOPY1}"
cmd2="echo \"Adding first conflict line\" >> $TFILE"
cmd4="svn ci -m \"Adding first conflict\""
cmd5="cd .."

echoPause "
Done. Causing user 1 to make a change and commit with::
$CSA$cmd1
$cmd2
$cmd4
$cmd5$CE"

$cmd1
pwd
eval $cmd2
eval $cmd4
$cmd5

cmd1="cd ${LCOPY2}"
cmd2="echo \"Adding second conflict line\" >> $TFILE"
cmd4="svn ci -m \"Adding second conflict\""
cmd5="cd .."

echoPause "
Done. Causing user 2 to make a change, and commit (that WILL FAIL), with:
$CSA$cmd1
$cmd2
$cmd4
$cmd5$CE"

$cmd1
pwd
eval $cmd2
eval $cmd4
$cmd5


cmd1="cd ${LCOPY2}"
cmd2="SVN_MERGE=${EXTTOOL} svn up"
cmd4="svn ci -m \"Adding second update - first conflict resolved\""
cmd5="cd .."

echoPause "
Done. Since user 2 commit has failed, we now do svn up, which will ask us to resolve the conflict.
Here we will call svn up with setting SVN_MERGE, which will call meld that will show a diff between:
* local version ('mine' - of user 2) on left
* remote version ('theirs' - of user 1) on right
note - marking the file as 'resolved' at the second 'svn up' prompt will upload a 'merged' version (with diff markers)!

$CSA$cmd1
$cmd2
$cmd4
$cmd5$CE

So the steps will be:
* Choose 'l' to launch external tool, when svn up discovers conflict and asks
* Make the changes via meld into the 'mine' $TFILE, and then save $TFILE and close meld.
* At the second prompt of svn up, choose 'mf' to accept 'mine-full' changes (as 'mine' file should now contain previous parts too, from meld) of $TFILE.


After that, a commit for user-2 will automatically be attempted..
"

$cmd1
pwd
eval $cmd2
eval $cmd4
$cmd5

cmd="svn log file://${ODIR}/${reponame}"
echoPause "
Done. Checking the current svn log with:
$CSA$cmd$CE"

$cmd

cmd="svn cat file://${ODIR}/${reponame}/${TFILE}"
echoPause "
Done. Looking at the latest revision of the file ${TFILE}:
$CSA$cmd$CE"

$cmd


echo -n "
Done - about to finish. Should I clean up (delete files?) (y/n) "
read answer
if [ $answer = "y" ]
then
    echo "Cleaning up: Deleting ${reponame}, ${LCOPY1}, ${LCOPY2}"
    rm -rf ${reponame}
    rm -rf ${LCOPY1}
    rm -rf ${LCOPY2}
fi

```
If you can't be bothered running the script, below is a sample output from it - which should also serve as a reminder:


> **"svn-conflict-external.sh output"]
svn-conflict-external.sh
simulate svn conflict interactively, by creating a local repo and tests
in dir: [COLOR=Green]/path/to/test[/COLOR]
[COLOR=Red]Press Enter to continue..[/COLOR]

Enter desired repo name and press [ENTER]: bla
Got repo name bla... About to run:
[COLOR=Blue]svnadmin create bla[/COLOR]
[COLOR=Red]Press Enter to continue..[/COLOR]

Created repo bla.
About to check out local copy for user 1 with
[COLOR=Blue]svn co file:///path/to/test/bla bla-1[/COLOR]
[COLOR=Red]Press Enter to continue..[/COLOR]

Checked out revision 0.
Populating and comitting local copy for user 1 with initial content with:
[COLOR=Blue]cd bla-1
echo "Starting content" > aTextFile.txt
svn add aTextFile.txt
svn ci -m "Initial content"
cd ..[/COLOR]
[COLOR=Red]Press Enter to continue..[/COLOR]

/path/to/test/bla-1
A         aTextFile.txt
Adding         aTextFile.txt
Transmitting file data .
Committed revision 1.

Done. Checking out rev.1 for user 2 (though we could have just done 'cp -a bla-1 bla-2') said:**
> svn co file:///path/to/test/bla bla-2[/COLOR]
[COLOR=Red]Press Enter to continue..[/COLOR]

A    bla-2/aTextFile.txt
Checked out revision 1.

Done. Causing user 1 to make a change and commit with::
[COLOR=Blue]cd bla-1
echo "Adding first conflict line" >> aTextFile.txt
svn ci -m "Adding first conflict"
cd ..[/COLOR]
[COLOR=Red]Press Enter to continue..[/COLOR]

/path/to/test/bla-1
Sending        aTextFile.txt
Transmitting file data .
Committed revision 2.

Done. Causing user 2 to make a change, and commit (that WILL FAIL), with:
[COLOR=Blue]cd bla-2
echo "Adding second conflict line" >> aTextFile.txt
svn ci -m "Adding second conflict"
cd ..[/COLOR]
[COLOR=Red]Press Enter to continue..[/COLOR]

/path/to/test/bla-2
Sending        aTextFile.txt
[COLOR=Red]svn: Commit failed (details follow):
svn: File '/aTextFile.txt' is out of date[/COLOR]

Done. Since user 2 commit has failed, we now do svn up, which will ask us to resolve the conflict.
Here we will call svn up with setting SVN_MERGE, which will call meld that will show a diff between:
* local version ('mine' - of user 2) on left
* remote version ('theirs' - of user 1) on right
note - marking the file as 'resolved' at the second 'svn up' prompt will upload a 'merged' version (with diff markers)!

[COLOR=Blue]cd bla-2
SVN_MERGE=~/meldwrap.sh svn up
svn ci -m "Adding second update - first conflict resolved"
cd ..[/COLOR]

So the steps will be:
* Choose 'l' to launch external tool, when svn up discovers conflict and asks
* Make the changes via meld into the 'mine' aTextFile.txt, and then save aTextFile.txt and close meld.
* At the second prompt of svn up, choose 'mf' to accept 'mine-full' changes (as 'mine' file should now contain previous parts too, from meld) of aTextFile.txt.


After that, a commit for user-2 will automatically be attempted..

[COLOR=Red]Press Enter to continue..[/COLOR]

/path/to/test/bla-2
[COLOR=Green]Conflict discovered in 'aTextFile.txt'.
Select: (p) postpone, (df) diff-full, (e) edit,
        (h) help for more options: **l**
Select: (p) postpone, (df) diff-full, (e) edit, (r) resolved,
        (h) help for more options: **mf** [/COLOR]
G    aTextFile.txt
Updated to revision 2.
Sending        aTextFile.txt
Transmitting file data .
Committed revision 3.

Done. Checking the current svn log with:
[COLOR=Blue]svn log file:///path/to/test/bla[/COLOR]
[COLOR=Red]Press Enter to continue..[/COLOR]

------------------------------------------------------------------------
r3 | TheUserName | 2010-03-11 16:39:44 +0100 (Thu, 11 Mar 2010) | 1 line

Adding second update - first conflict resolved
------------------------------------------------------------------------
r2 | TheUserName | 2010-03-11 16:39:11 +0100 (Thu, 11 Mar 2010) | 1 line

Adding first conflict
------------------------------------------------------------------------
r1 | TheUserName | 2010-03-11 16:39:02 +0100 (Thu, 11 Mar 2010) | 1 line

Initial content
------------------------------------------------------------------------

Done. Looking at the latest revision of the file aTextFile.txt:
[COLOR=Blue]svn cat file:///path/to/test/bla/aTextFile.txt[/COLOR]
[COLOR=Red]Press Enter to continue..[/COLOR]

Starting content
Adding first conflict line
Adding second conflict line

Done - about to finish. Should I clean up (delete files?) (y/n) y
Cleaning up: Deleting bla, bla-1, bla-2



---


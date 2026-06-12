---
title: "cp and mv command - nuanced instructions"
date: 2014-02-17
forum: New to Ubuntu
---

### Post by aaron.kyle on 2014-02-17
Hello and thank you for reading this.

I have consulted several resources about the cp command, such as: [http://www.computerhope.com/unix/ucp.htm](http://www.computerhope.com/unix/ucp.htm).  I still can't find my answer.

What I would like to do is to move files from one folder to another, replacing the existing contents ONLY IF the time signatures are identical.  Otherwise I would like to move the file but to keep both copies (name.file and name.file(2) ..or something equivalent).  Any suggestions for how I might accomplish this?

Thanks again!

---

### Post by fromite on 2014-02-17
> **aaron.kyle said:**
> Hello and thank you for reading this.

I have consulted several resources about the cp command, such as: [http://www.computerhope.com/unix/ucp.htm](http://www.computerhope.com/unix/ucp.htm).  I still can't find my answer.

What I would like to do is to move files from one folder to another, replacing the existing contents ONLY IF the time signatures are identical.  Otherwise I would like to move the file but to keep both copies (name.file and name.file(2) ..or something equivalent).  Any suggestions for how I might accomplish this?

Thanks again!

So just to clarify, you want to overwrite the files with the same time signature but keep both copies if they are not identically timed? I know you can do the later, im not sure about the first. I will check on this now and get back to you shortly. Please correct me if I'm misunderstanding something thought!

~Zeus

---

### Post by fromite on 2014-02-17
> **aaron.kyle said:**
> Hello and thank you for reading this.

I have consulted several resources about the cp command, such as: [http://www.computerhope.com/unix/ucp.htm](http://www.computerhope.com/unix/ucp.htm).  I still can't find my answer.

What I would like to do is to move files from one folder to another, replacing the existing contents ONLY IF the time signatures are identical.  Otherwise I would like to move the file but to keep both copies (name.file and name.file(2) ..or something equivalent).  Any suggestions for how I might accomplish this?

Thanks again!

From what I could try/find/etc the best method, which I'm sure isn't the best since I'm still learning myself, would be to navigate to the directory you want and do ls -l to view a long version list of the contents. 
Then run:
cp -a -i -u directoryOfFilesToMove/* directoryFilesAreMovedTo

example: if i wanted to move all files from StupidTest to StupidTestDir I would use:

cp -a -i -u StupidTest/* StupidTestDir

This copies all file attributes (incl ownerships and permissions) to the new directory (-a    archive), prompts for overwrites if there are files with the same name (-i   interactive), and copies only the files that either don't exist or are newer than the existing files in the destination directory (-u    update). 
Using -u kind of defeats the purpose of using -i or even viewing the contents of the directory; however, if you wanted to manually check against the update you could (kind of unnecessary though). 

To answer the question regarding overwriting files if the timestamps match: I added the -i in there that way you can control the files you didn't want to overwrite, which is also why i suggested using ls -l from within the directories you are transferring files to and from to see their time stamps. Thought I'm sure another user more adept in shell-foo will have a more streamlined approach.

Please let me know if this answers your question or if I further confused things. Hopefully it helped.

~Zeus


**edit: added the example I intended to use the first time I posted
**edit#2: added what I actually edited (sorry still kind of new to helping others)
***edit#3: added the "answer" to his question

---

### Post by Jonathan Precise on 2014-02-17
If by time signatures mean the time it was created, then these two scripts will work.

This can be done via the test/[ command to determine whether or not to replace the file. (The command can be called 'test' or '[' <--that's a bracket)

Open the text editor and put in the following (if you want a text interface):

> **Jonathan Precise]
```

#! /bin/bash
# Uses the cp and mv commands

#clear # Clear the console window (disabled)
echo "" 1>&2 # Blank line (echoed to stderr)
echo -n "Where is the original file located? " # Text saying "Where is the original file located? "
read TPOTOF # Read from stdin where the path of the original file is, and save the path to '$TPOTOF'
echo "" # Blank line
echo -n "Where is the newdirectory located? " # Text saying "Where is the original file located? "
read TPOTNF # Read from stdin where the path of the original file is, and save the path to '$TPOTOF'
if [ -z $TPOTNF ] || [ -z $TPOTOF ] # If one of the values are [null], then
then
    echo "E:One or more of the values you have entered are empty" # State the error
    exit 1 # Exit with error code 1
elif [ ! -f $TPOTOF ] || [ ! -d $TPOTNF ] #Or if one of the files do not exist, then
then
    echo "E:One or more of the files you specified do not exist." # State the error
    exit 2 # Exit with error code 2
fi
TPOTNF="$TPOTNF/$TPOTOF"
if [ -f $TPOTNF ]
then
    if test $TPOTOF -nt $TPOTNF || test $TPOTOF -ot $TPOTNF
    then
        echo "Time stamps are different. Will not overwrite file."
        cp $TPOTOF `echo "new-"$TPOTNF`
    else
        echo -n "W: Time stamps are the same. Are you sure you want to overwrite? This can not be undone. [y/N]: "
        read YesNo
        case $YesNo in
            y|Y|yes|Yes|yEs|yeS|YEs|YeS|yES|YES)
                echo "Ok. Doing as you wished." said:**
> 

Or for a graphical interface:

[QUOTE=Jonathan Precise]
```

#! /bin/bash
# Uses the cp and mv commands

#clear # Clear the console window (disabled)
TPOTOF=`zenity --entry --title="Made with zenity" --text="Where is the original file located? "`
TPOTNF=`zenity --entry --title="Made with zenity" --text="Where is the newdirectory located? "`
if [ -z $TPOTNF ] || [ -z $TPOTOF ]
then
    zenity --error --title="Error | Made with zenity" --text="E:One or more of the values you have entered are empty" --no-wrap
    exit 1
elif [ ! -f $TPOTOF ] || [ ! -d $TPOTNF ] #Or if one of the files do not exist, then
then
    zenity --error --title="Error | Made with zenity" --text="E:One or more of the files you specified do not exist." --no-wrap
    exit 2
fi
TPOTNF="$TPOTNF/$TPOTOF"
if [ -f $TPOTNF ]
then
    if test $TPOTOF -nt $TPOTNF || test $TPOTOF -ot $TPOTNF
    then
        zenity --info --title="Made with zenity" --text="Time stamps are different. Will not overwrite file."
        cp $TPOTOF `echo "new-"$TPOTNF`
    else
        zenity --question --title="Warning | Made with zenity" "W: Time stamps are the same. Are you sure you want to overwrite? This can not be undone."
        if [ $? != 0 ]
        then
            zenity --info --title="Made with zenity" --text="Ok. Doing as you wished."; sleep 1
            rm -rf $TPOTNF ;
            cp $TPOTOF $TPOTNF ;
            zenity --info --title="Mission Complete\! | Made with zenity" --text='Done!'
        else
            zenity --info --title="Made with zenity" --text="Ok. Will not replace file.";
        fi
    fi
else
    zenity --info --title="Made with zenity" --text="The file does not exist in the remote directory, so it will just be copied."
    cp $TPOTOF $TPOTNF
fi
echo "Will now exit" ; sleep 3
exit 0

```


Then make the saved file executable, and execute the script.

Hope it's of help.

---

### Post by fromite on 2014-02-17
And that, ladies and gentlemen, is script-foo. Definitely made me appear as the noob I am :P

Well done!

P.s. What languange is that? Seems like a short-hand version of C with nix commands thrown in

---

### Post by Jonathan Precise on 2014-02-17
> **fromite said:**
> What languange is that? Seems like a short-hand version of C with nix commands thrown in

It's using the BASH shell (**B**ourne **A**gain **SH**ell)

---

### Post by fromite on 2014-02-17
> **Jonathan Precise said:**
> It's using the BASH shell (**B**ourne **A**gain **SH**ell)

Know of any good educational references?

---

### Post by Dave_L on 2014-02-17
> **fromite said:**
> Know of any good educational references?

[http://manpages.ubuntu.com/manpages/precise/en/man1/bash.1.html](http://manpages.ubuntu.com/manpages/precise/en/man1/bash.1.html)
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

---

### Post by G_Ajith_Kumar on 2014-02-17
Hi,  A very good tutorial for Shell Scripts. [http://linuxcommand.org/writing_shell_scripts.php](http://linuxcommand.org/writing_shell_scripts.php)

Scripting is the power of Linux!!!!!!!

Good Luck.

---

### Post by fromite on 2014-02-17
Thanks guys, perciate it!

---

### Post by Habitual on 2014-02-18
> **fromite said:**
> Know of any good educational references?

Well. since you asked :)

Various Linux Guides I have collected:
[http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html) 
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html) 
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/)
[http://www.gnu.org/software/bash/manual/html_node/index.html](http://www.gnu.org/software/bash/manual/html_node/index.html)
[http://www.grymoire.com/Unix/Sh.html](http://www.grymoire.com/Unix/Sh.html)
[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)
[http://tldp.org/LDP/abs/abs-guide.pdf](http://tldp.org/LDP/abs/abs-guide.pdf)
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/) 
[http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)
[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)
[http://mylinuxbook.com/linux-shell-environment/](http://mylinuxbook.com/linux-shell-environment/)
[http://www.subsignal.org/doc/AliensBashTutorial.html#Table%20Of%20Contents](http://www.subsignal.org/doc/AliensBashTutorial.html#Table%20Of%20Contents)
[http://www.rigacci.org/docs/biblio/offline/TLCL-09.12.pdf](http://www.rigacci.org/docs/biblio/offline/TLCL-09.12.pdf)
[http://www.linuxhomenetworking.com/](http://www.linuxhomenetworking.com/)
[http://mylinuxbook.com/bash-shell-scripting-part-i/](http://mylinuxbook.com/bash-shell-scripting-part-i/)
[http://mylinuxbook.com/bash-shell-scripting-2/](http://mylinuxbook.com/bash-shell-scripting-2/)
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)
[http://linuxcommand.org/lc3_learning_the_shell.php](http://linuxcommand.org/lc3_learning_the_shell.php)
[http://unixhelp.ed.ac.uk/](http://unixhelp.ed.ac.uk/)
[http://www.linuxquestions.org/questions/blog/druuna-60084/resources-useful-links-35334/](http://www.linuxquestions.org/questions/blog/druuna-60084/resources-useful-links-35334/)
[http://www.linuxquestions.org/questions/linux-general-1/links-for-helpful-linux-articles-and-books-4175433508/](http://www.linuxquestions.org/questions/linux-general-1/links-for-helpful-linux-articles-and-books-4175433508/)
[http://www.hammondslegacy.com/forum/viewforum.php?f=40&sid=5859bbcf18ccb151f7de3e86cafdf486](http://www.hammondslegacy.com/forum/viewforum.php?f=40&sid=5859bbcf18ccb151f7de3e86cafdf486)
[http://linux-shell-commands.jimdo.com/](http://linux-shell-commands.jimdo.com/)
[http://flossmanuals.net/command-line](http://flossmanuals.net/command-line)
[http://tille.garrels.be/training/tldp/](http://tille.garrels.be/training/tldp/)
[http://www.collegeathome.com/blog/2008/05/22/open-courseware-for-linux-geeks-50-resources/](http://www.collegeathome.com/blog/2008/05/22/open-courseware-for-linux-geeks-50-resources/)
[http://www.codecoffee.com/tipsforlinux/index-linux.html](http://www.codecoffee.com/tipsforlinux/index-linux.html)
[http://www.linuxquestions.org/questions/blog/rtmistler-575248/bash-scripting-for-dummies-and-geniuses-35795/](http://www.linuxquestions.org/questions/blog/rtmistler-575248/bash-scripting-for-dummies-and-geniuses-35795/)
[http://www.google.com/cse/home?cx=016212844476379046035:zj-1bdfg5ga&hl=en](http://www.google.com/cse/home?cx=016212844476379046035:zj-1bdfg5ga&hl=en)

---

### Post by Vaphell on 2014-02-18
that script is very very sloppy. Not a single variable in the whole script is protected by double-quotes against word splitting, so it will blow up on anything with whitespace in it.

```
cp $TPOTOF `echo "new-"$TPOTNF`
```
o.O why not ```
cp "$TPOTOF" "new-$TPOTNF"
```?

backticks `` are on their way out (deprecated) and $() should be used instead.

---

### Post by aaron.kyle on 2014-02-24
Hi and thanks to all for responding!  Sorry I haven't replied sooner; I had a bit of a family emergency and am just now back behind the computer.  Tomorrow I will try some of these solutions.  I just didn't want more time to pass before saying thanks to all!

---

### Post by aaron.kyle on 2014-02-24
Your understanding of my question was absolutely correct.  I apologize for the delayed reply; just after I wrote this I got called away due to an illness in my family.  Thank you so much for your time and help!

---

### Post by aaron.kyle on 2014-02-24
Zeus, thank you.  My hope is to accomplish something slightly different.  If I have 600 files in a directory that I wish to overwrite, I don't want to manually validate all of them.  Sometimes, too, the older version of a file has information or changes that I wish to keep, such as sometimes happens when collaborating on a file and someone emails it back to me with changes using the same name as the name I gave that same file -- resulting if different timestamps for different docs, each of which should be preserved.

Imagine, for instance, that I circulate a file called text,v2.txt, then save it as text,v2-edit.txt  and a colleague emails me another file called text,v2-edit.txt.  We both have contributed edits, and just copying in the new file would overwrite one of our contributions.  In this case, I'd like to preserve both, but to flag it as some sort of conflict or duplicate -- like text,v2-edit(2).txt (or something).

---

### Post by aaron.kyle on 2014-02-24
Jonathan,

Thanks!  That is a useful looking script.  I'll try it. Just to be clear, however, I would also be concerned with date modified.  Any ways to tweak the script accordingly?

---

### Post by Bucky Ball on 2014-02-24
> **Vaphell said:**
> that script is very very sloppy. Not a single variable in the whole script is protected by double-quotes against word splitting, so it will blow up on anything with whitespace in it.

```
cp $TPOTOF `echo "new-"$TPOTNF`
```
o.O why not ```
cp "$TPOTOF" "new-$TPOTNF"
```?

backticks `` are on their way out (deprecated) and $() should be used instead.

Unsure if you read this.

---

### Post by aaron.kyle on 2014-02-24
Thank you, Bucky Ball.  I did indeed read it.  I will follow your suggestion and will try to clean up the script a little before implementing it.  To be frank, the script is a bit daunting for me, so I'll need some time to digest it.  I'm still interested in a means of accomplishing a 'create conflict' option for files based on date modified as well as date created.  I simpler script would certainly be appealing.  I am surprised that there isn't a more straight-forward command out there... unless there is something I am missing?

---

### Post by aaron.kyle on 2014-02-24
Maybe I am going about the the wrong way.  Should I be working not with cp and mv, but with svn?

---

### Post by CharlesA on 2014-02-24
I'm probably going to get yelled at for this, but when I first started shell scripting, I used all caps for variables, but now I either use all lowercase or CamelCase so I don't accidentally override system variables (even if that is unlikely).

---

### Post by aaron.kyle on 2014-02-25
hi Charles, and thank you for the suggestion (of sorts?).  I am not experienced enough to know why anyone would yell at you; sounds reasonable to me.

... Any proposed edits to Jonathan's script to accommodate 'date modified'?

Thanks again to everyone who has contributed here!

---

### Post by CharlesA on 2014-02-25
I'd probably look into using find to deal with modified date, but I don't know how to integrate it into the script Jonathan posted.

---

### Post by aaron.kyle on 2014-03-12
Thanks again to all.

I continue to learn.  I'll update this post once I've finished my investigations.  I really appreciate all the support!

---


---
title: "Bash: When to sudo"
date: 2009-04-15
forum: Programming Talk
---

### Post by Jesdisciple on 2009-04-15
My bash script retrieves some SVN modules from the GNOME site for patching.  It then copies the files to a second directory so the user can edit the second copy and generate a diff.  But when I copy the files, if I didn't sudo the script I get "permission denied" errors about the SVN files, all of which are read-only by default.

I'm not sure whether diff looks at hidden directories (like .svn), but regardless the "permission denied" errors are just ugly.  So I tried sudo'ing my script, but then all the files are owned by root and my [xdg-open]("http://ubuntuforums.org/showthread.php?t=1125916") command throws a warning and an error instead of opening Nautilus:```
Warning: unknown mime-type for "gnome-pilot/new" -- using "application/octet-stream"
Error: no "view" mailcap rules found for type "application/octet-stream"
```

sudo is also undesirable for most of the script simply because it's not needed.  So I'm wondering how I can select which parts get root privileges. (I know that sudo allows activity as users other than root.)  For example, can functions be sudo'ed?  Here's the entire script in case it matters, right after the command I'm using to test it...

Oh, and before I'm typing so far down my post that you might not look:  Thanks!```
./setup.sh -n gnome-pilot -m "gnome-pilot gnome-pilot-conduits" -v
``````
#!/bin/bash
usage(){
cat << EOF
usage: $0 options

This script creates a new directory structure for a GnomeLove project.

OPTIONS:
   -h      Optional; Show this message and ignore other flags
   -n      Name for the new project folder, and default module to checkout
   -m      Optional; module(s) to checkout, in quotes if plural
   -v      Optional; verbose
EOF
}

NAME=
MODULES=
VERBOSE=0
while getopts “hn:m:v” OPTION
do
     case $OPTION in
         h)
             usage
             exit 1
             ;;
         n)
             NAME=$OPTARG
             ;;
         m)
             MODULES=$OPTARG
             ;;
         v)
             VERBOSE=1
             ;;
         ?)
             usage
             exit
             ;;
     esac
done

if [[ -z $NAME ]]; then
     usage
     exit 1
fi

if [[ -z $MODULES ]]; then
	MODULES=$NAME
fi

if [ ! -d "$NAME" ]; then
	mkdir $NAME
fi
if [ ! -d "$NAME/old" ]; then
	mkdir $NAME/old
fi
if [ ! -d "$NAME/new" ]; then
	mkdir $NAME/new
fi

declare -a modules
modules=(`echo $MODULES`)

for s in ${modules[@]}; do
	url="http://svn.gnome.org/svn/$s/trunk"
	if [ $VERBOSE ]; then
		echo
		echo "Checking out module '$s' from $url."
	fi
	svn co $url "$NAME/old/$s"
	
	if [ $VERBOSE ]; then
		echo
		echo "Copying module '$s' from 'old' to 'new' directory."
	fi
	cp -r "$NAME/old/$s" "$NAME/new"
done

if [ $VERBOSE ]; then
	echo
	echo "Opening file browser to 'new' directory."
fi
xdg-open "$NAME/new"

echo
echo "After fixing the 'new' files, run the command './patch.sh $NAME' to complete the process."
```

---

### Post by squaregoldfish on 2009-04-15
You can add sudo to any commands that require it within your script. The first time a sudo command is encountered, you'll be asked for your password; any subsequent sudo commands will remember your password and not ask for it again.

Steve.

---

### Post by Jesdisciple on 2009-04-15
Thanks for the response.  I got my parenthetical edit in late, which is why you didn't know that I already know all that.

Can functions or other blocks of code be sudo'ed?  If I sudo the script to root and sudo a function back to myself, can I sudo a line within that function back to root without entering a password?

---

### Post by Arndt on 2009-04-15
> **Jesdisciple said:**
> Thanks for the response.  I got my parenthetical edit in late, which is why you didn't know that I already know all that.

Can functions or other blocks of code be sudo'ed?  If I sudo the script to root and sudo a function back to myself, can I sudo a line within that function back to root without entering a password?

Isn't it better to tell 'diff' to ignore the .svn files (that can be done), or not copy them in the first place (or remove them from the target before copying)? Use root privileges only when really necessary (because just a little sloppiness can ruin very much).

---

### Post by Jesdisciple on 2009-04-15
I managed to delete the .svn directories, but now I wonder whether any problems would arise if the copy became outdated before the patch was submitted (which SVN wouldn't know).  I guess the human reviewer would solve this by rejecting the patch and asking for another?

I also dislike the message that I get when running the script again without deleting everything previously downloaded, although it's only printed once per call.  Should I make sure the 'old' and 'new' directories are empty first?  I think that would also solve the above syncing problem.> svn: Failed to add file [...]: object of the same name already exists

Thanks!

---

### Post by Jesdisciple on 2009-04-15
I wonder if the *[svn diff]("http://svnbook.red-bean.com/nightly/en/svn-book.html#svn.forcvs.disconnected")* command would be useful when I have more than one module...  Wouldn't I have to correct the output paths?

I just tried a different approach which halfway worked...  I gave myself rw permissions on the SVN files, but then I got a "cannot stat" error from *cp* instead of "cannot create regular file."  Where is the new error coming from?

I also realized that the "permission denied" errors only occur when I'm overwriting the files.  (I thought files couldn't be created by a user to whom they would be read-only.)  So the problem to be solved is purely one of syncing with the SVN repository.

---


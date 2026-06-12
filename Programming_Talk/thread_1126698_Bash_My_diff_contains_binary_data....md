---
title: "Bash: My diff contains binary data...?"
date: 2009-04-15
forum: Programming Talk
---

### Post by Jesdisciple on 2009-04-15
[Issue history.]("http://ubuntuforums.org/showthread.php?p=7076521")  (I was trying to stay in that thread, but I think this is sufficiently off-topic to have its own.)

My diff contains binary data; I have no idea why unless it's that the two directories are identical (but I should think diff wouldn't choke because of that).  I'm just testing this script, and that's why I'm not changing anything.

I tried Googling this but came up empty.  I should probably note that my system is decaying and sometimes does very strange things; most of these things stop when something different happens.  (For example, a program which hung in Valgrind and GDB no matter how many times I recompiled it started working much better when I ran it normally and then recompiled.)  I haven't yet been able to use a CD burner to get a Live CD yet.  Also, I got valid diff output for these same Gnome modules earlier, after I had modified one copy - but that was with a manual call to diff.

Note: I'm posting the scripts in reverse order because patch.sh is the one more directly involved in this question.

Thanks!```
./patch.sh gnome-pilot
``````
#!/bin/bash
diff -x .*/\.svn/.* -Naur $1/old $1/new > $1/patch.diff
```

```
./setup.sh -n gnome-pilot -m "gnome-pilot gnome-pilot-conduits"
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
while getopts &#8220;hn:m:v&#8221; OPTION
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

if [ $VERBOSE -eq 1 ]; then
	echo
	echo "Creating absent directories."
fi
if [ ! -d "$NAME" ]; then
	mkdir $NAME
fi
if [ ! -d "$NAME/old" ]; then
	mkdir $NAME/old
fi
if [ -d "$NAME/new" ]; then
	if [ $VERBOSE -eq 1 ]; then
		echo
		echo "Emptying 'new' directory."
	fi
	rm -rf `ls $NAME/new`
else
	mkdir $NAME/new
fi

declare -a modules
modules=(`echo $MODULES`)

for s in ${modules[@]}; do
	url="http://svn.gnome.org/svn/$s/trunk"
	if [ $VERBOSE -eq 1 ]; then
		echo
		echo "Checking out module '$s' from $url."
	fi
	svn co $url "$NAME/old/$s" -q
	
#conditional comments for testing
if [ 0 -eq 1 ]; then
	if [ $VERBOSE -eq 1 ]; then
		echo
		echo "Deleting SVN administrative directories."
	fi
	find "$NAME/old/$s" -depth -name .svn -type d -print0 | xargs -0 rm -rf
#else
	if [ $VERBOSE -eq 1 ]; then
		echo
		echo "chmod'ing SVN administrative directories."
	fi
	svn=$(find "$NAME/new/$s" -depth -name .svn -type d)
	chmod u=rw $svn
	chmod g=rw $svn
fi
	
	if [ $VERBOSE -eq 1 ]; then
		echo
		echo "Copying module '$s' from 'old' to 'new' directory."
	fi
	cp -r "$NAME/old/$s" "$NAME/new"
done

if [ $VERBOSE -eq 1 ]; then
	echo
	echo "Opening file browser to 'new' directory."
fi
xdg-open "$NAME/new"

echo
echo "After fixing the 'new' files, run the command './patch.sh $NAME' to complete the process."
```

---


---
title: "Shell getopts command is dangerous!"
date: 2007-01-02
forum: Programming Talk
---

### Post by cosmolee on 2007-01-02
GNU bash, version 3.1.17(1)

In learning the `getopts` command, I'm discovering some things that I find disturbing.  I wanted to post this to get some feedback from anyone.  

getopts is NOT very smart.  I'd say it's downright dangerous.  Users should be warned of it's pitfalls.  While `getops` may be a POSIX standardized program, it certainly doesn't seem very smart or reliable.  It may be meant to make argument processing easier, but it seems to make it more dangerous, by opening error-prone holes in argument processing!  


$ cat getopts-test.sh

while getopts a:bcdefg OPT      #require an argument for "-a"
do
        echo OPT is $OPT, OPTARG is $OPTARG, and OPTIND is $OPTIND .
done

$



Here, we pass the "-a" option an argument (file1), as required and indicated to getopts option_spec (a:bcdefg).  It works as expected.

$ ./getopt* -a file1 -b -c -d -e
OPT is a, OPTARG is file1, and OPTIND is 3 .
OPT is b, OPTARG is , and OPTIND is 4 .
OPT is c, OPTARG is , and OPTIND is 5 .
OPT is d, OPTARG is , and OPTIND is 6 .
OPT is e, OPTARG is , and OPTIND is 7 .




Here, the -a option requires an argument be passed to it.  However, if one isn't, getopts mistakes the next option (-b) as the argument to the option "-a", even though "-b" starts with a "-" indicating it is an option.  So, this option (-b) goes completely undetected.


$ ./getopt* -a -b -c -d -e
OPT is a, OPTARG is -b, and OPTIND is 3 .
OPT is c, OPTARG is , and OPTIND is 4 .
OPT is d, OPTARG is , and OPTIND is 5 .
OPT is e, OPTARG is , and OPTIND is 6 .



Here, we "accidentally" pass an argument to the second option (-b), but getops doesn't notice the error.  Again, it mistakes the "-b" option to be an argument to the "-a" option.  The remaining options, "-c", "-d", & "-e" are ignored!

$ ./getopt* -a  -b file2 -c -d -e
OPT is a, OPTARG is -b, and OPTIND is 3 .

These last two could be fatal if "-b" was, say, an option for "noclobber" or something like that.


Here we pass arguments to both "-a" and "-b".  getopts doesn't notice that "-b" has been erroneously given an argument, and "-c", "-d", & "-e" are ignored!

$ ./getopt* -a file1 -b file2 -c -d -e
OPT is a, OPTARG is file1, and OPTIND is 3 .
OPT is b, OPTARG is , and OPTIND is 4 .



So, is `getopts` really worth using?  Any comments?

---

### Post by slavik on 2007-01-02
sometimes you might want your option to get a dash ...

like for the -f option of tar, a dash means stdin/stdout (depending on whether is -x or -c is used)

---

### Post by cosmolee on 2007-01-02
Correct me if I'm wrong, but I don't think `getopts` would even see such a dash.  That kind of dash would be processed by the shell as a redirection, before the options are processed by the program being run.

---

### Post by menachem on 2010-07-08
It's obviously been a while since this thread was started, but I've just come across this problem. Here is the relevant excerpt from my script:

```
while getopts ":d:frhls" options #http://wiki.bash-hackers.org/howto/getopts_tutorial
do
	case $options in
	f ) 	#Force Download even if already downloaded
        	FORCE=yes
        	;;
	r )	#Download and process RSS feed.
		DO_RSS=yes
		;;
	h ) 	echo Download and Convert lectures from torahcafe.com
		echo "Usage: $0 [-h] [-f] [-l] [-r] [-s] [-d dir] [url ...]"
		echo -f: Force Download even if already downloaded
		echo -l: Exit after viewing Download Log
		echo -r: Download latest RSS Feed and get all new files
		echo -s: Exit after Viewing Log of Successful downloads
		echo -d: Specify download directory
		echo -h: Help
        	;;
	l ) 	# View download log and exit
		clear
		cat $log
		exit 0
		;;
	s ) 	# View Success log and exit
		clear
		cat $SUCCESS_LOG
		exit 0
        	;;
	d ) 	# Establish destination directory
		DLOAD_DIR="$OPTARG"
		#exit 1
        	;;
	\? ) 	# We will ignore invalid options
		echo "Invalid option: -$OPTARG"
		#exit 1
        	;;
	: )
		echo "Option -$OPTARG requires an argument."
		echo 'run "$0 -h" to see valid options'
		exit 1
		;;
	esac

```

Everything was working fine until I added the -d switch. The -d switch demangs an argument and if I give it an argument everything is fine.

When I don't give it an argument I would expect it to realize that I didn't give it an argument, and run the ":" option. Instead, it takes the next variable as the $OPTARG for "-d"

In other words:
./script -r -d $HOME -- works properly
./script -r -d -- gives an error
./script -d -r -- erroneously assigns "-r" as the $OPTARG for "-d"

This is what you (cosmolee) described in your post. 

Did you solve this issue? What kind of workaround did you use? I'm thinking I may have to write something into the script that will explicitly check if -d has an argument, and if not exit before even going through the getopts.

---

### Post by geirha on 2010-07-08
This is pretty standard behavior. Take the tar command for instance, if you do the same with its -f option, it fails in the same way.
```

$ tar -f -x
tar: You must specify one of the `-Acdtrux' options
Try `tar --help' or `tar --usage' for more information.

```
It used the -x as argument to -f, and thus didn't consider -x to be an option...

Put in another way, what if you'd want your -d option to take an argument that starts with a -? That would be impossible if it behaved the way you expected.

See [http://mywiki.wooledge.org/BashFAQ/035](http://mywiki.wooledge.org/BashFAQ/035) for some examples on how to parse command-line options also without using getopts.

---

### Post by menachem on 2010-07-08
Here's the code I threw together to make sure that the argument after the '-d' switch was not another switch.

I placed this in my script before the getopts stuff:

```
#This monstrosity makes sure that the entry after $sw on the command line
#Is not another option. This case falls through getopts cracks.
# see here for more info: http://ubuntuforums.org/showthread.php?p=9562220
pars=
sw='-d'
if [[ `echo "$*"|grep -- "$sw"` != "" ]];then
        pars=( "$@" ) #create an array to store all command line options
        for i in `seq 0 $((${#pars[*]}-1))` #one less than the number of elements in array
        do
                #really confusing way of seeing if first char in array element after "$sw" is a '-'
                if [[ "${pars[$i]}" == "$sw" && "${pars[$((${i}+1))]:0:1}" == "-"  ]];then
                        echo "$sw needs an argument."
                        echo run "$0 -h" for more information
                        exit 4
                fi
        done
fi
```

I realize now that I should have used a while loop instead of a for loop to cycle through the elements of the array (if only for readability), but this works.

EDIT:
Here is a much more sane way to check if the argument to -d starts with a "-":

```
        d )     # Establish destination directory
                if [[ "${OPTARG:0:1}" != "-" ]];then # argument to -d was used
                        DLOAD_DIR="$OPTARG"
                else
                        echo "-d needs an argument."
                        exit 4
                fi
                ;;

```

---

### Post by geirha on 2010-07-08
If someone is stupid enough to run the script with
```
./script -d -r
```
even though your script specifically states that -d takes a path as argument, then why bother checking for it?. Just assume -r is the path to use, check if it exists, and then bail out with a message like "-r: No such file or directory"

---

### Post by StephenF on 2010-07-08
Computers are not very good at guessing. If they were they would have achieved the ability to think for themselves and would be [s]running[/s] ruining our lives for us.

Lets leave the power in the hands of the users to shoot themselves in the foot if they must. At least it will be a learning experience from which they can grow.

At the very least, getopts has no business knowing the context of command line parameters.

---

### Post by menachem on 2010-07-08
> **geirha said:**
> If someone is stupid enough to run the script with
```
./script -d -r
```
even though your script specifically states that -d takes a path as argument, then why bother checking for it?. Just assume -r is the path to use, check if it exists, and then bail out with a message like "-r: No such file or directory"

I check for it because, as the saying goes, "Make something idiot proof and someone will make a bigger idiot". When writing a script I always try to figure out how people will mess it up and then I try to make sure they can't do it. I'm usually still surprised.

Also, in the script the user has an option to override the default destination directory (using the -d switch). If the directory does not exist, the script will create it. That's why I can't just use your suggestion to check later if the directory exists.

In the code snippet below, you can see that I just ignore an invalid command line switch (instead of exiting with an error), because, as you suggested, I don't care if they put an invalid switch, since the script will later filter it out. That won't work in the case of the '-d' switch, as explained above.

---


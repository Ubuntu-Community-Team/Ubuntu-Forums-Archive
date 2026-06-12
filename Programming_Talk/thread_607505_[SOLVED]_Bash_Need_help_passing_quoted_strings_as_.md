---
title: "[SOLVED] Bash: Need help passing quoted strings as args"
date: 2007-11-09
forum: Programming Talk
---

### Post by dwhitney67 on 2007-11-09
Hello everyone,

I am writing the most ridiculous script to satisfy a request from my manager at the office.  He wants to allow individual s/w developers to be able to check-out files from CVS, and then have such files code-beautified to the user's liking.

Upon committing a file back to CVS, the manager requested that the software be code-beautified back to the company's liking.

Thus I have set off to write a script that will encapsulate the beautification process and the CVS functionalities.  The man-page for CVS indicates that it accepts four types of command-line types

1. cvs option(s)
2. cvs command
3. cvs command option(s)
4. cvs args (e.g. files or directories)

I written a script that parses these (well, not all, but the commonly used options and command options), and I am able to produce the following when invoking my script:

```
$ cvswrap commit -m "where are my quotes." someFile.cpp
DEBUG...... OPS     = 
DEBUG...... CMD     = commit
DEBUG...... CMD_OPS =  -m "where are my quotes."
DEBUG...... ARGS    = TCPSocket.cpp __EndArg__
cvs commit: nothing known about `are'
cvs commit: nothing known about `my'
cvs commit: nothing known about `quotes."'
cvs [commit aborted]: correct above errors first!

```

**Question:**  Does anyone know how to pass CMD_OPS such that CVS see's it exactly as I see it when it is printed out?

I've tried additional (escaped) quotes, brackets, etc, but either I produce a syntax error in the script or the behavior remains the same.

Here's a partial listing of my script:
```
# Break apart the command line arguments into individual types
#
# 1. get CVS options
#
OPTIND=1
while getopts "d:" options
do
        case $options in
            d ) OPS="$OPS -d $OPTARG";;
        esac
done

# 2. get the command
#
OPTIND=$OPTIND-1
shift $OPTIND
CMD=$1;
shift 1

# 3. get command-options
#
OPTIND=1
while getopts "D:m:r:" options
do
        case $options in
            D ) CMD_OPS="$CMD_OPS -D $OPTARG";;
            m ) CMD_OPS="$CMD_OPS -m \"$OPTARG\"";;
            r ) CMD_OPS="$CMD_OPS -r $OPTARG";;
        esac
done

# 4. get args
#
OPTIND=$OPTIND-1
shift $OPTIND
ARGS="$* __EndArg__"


echo "DEBUG...... OPS     = $OPS"
echo "DEBUG...... CMD     = $CMD"
echo "DEBUG...... CMD_OPS = $CMD_OPS"
echo "DEBUG...... ARGS    = $ARGS"

...

# Pick apart the cvs arg(s)
#
declare -i FIELD=1
TOKEN=`echo $ARGS | cut -d ' ' -f$FIELD`

while [ "$TOKEN" != "__EndArg__" ]
do
        # 1. Find all C++ source files in TOKEN so that they can
        #    be beautified to the company's code style.
        BeautifySourceFiles $TOKEN $CMP_BEAUTY_CONFIG

        # 2. CVS commit TOKEN; then check for error
        $REAL_CVS $OPS $CMD $CMD_OPS $TOKEN

        if [ $? -eq 0 ]
        then
                # 3. No error; Find all C++ source files in TOKEN so that
                #    they can be beautified to the user's code style.
                BeautifySourceFiles $TOKEN $USER_BEAUTY_CONFIG
        else
                exit 1
        fi

        # Get the next token
        #
        FIELD=$FIELD+1
        TOKEN=`echo $ARGS | cut -d ' ' -f$FIELD`
done
```

---

### Post by PaulFr on 2007-11-09
Did you try ```
eval $REAL_CVS $OPS $CMD $CMD_OPS $TOKEN
``` instead of ```
$REAL_CVS $OPS $CMD $CMD_OPS $TOKEN
``` ?

---

### Post by dwhitney67 on 2007-11-09
Thanks a lot; that worked!  I never knew that 'eval' could be used for such purpose.  I always thought it was used to test something.

---


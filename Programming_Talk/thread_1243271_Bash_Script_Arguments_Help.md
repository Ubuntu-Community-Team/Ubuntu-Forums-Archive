---
title: "Bash Script Arguments Help"
date: 2009-08-18
forum: Programming Talk
---

### Post by Mizutsuki on 2009-08-18
Hello,

I'm trying to write what should be a fairly simple bash script right now, but I've never written in BASH before so I needed help setting up the command line interpretation.

The script is used to re-encode videos into a format that is slightly nicer on my display hardware, and I don't really have any problems with the video encoding stuff, it's just the command line.  I want to be able to say something like this:
```
resize.sh -crf 21 movie.mkv television\ show\ ep*.mkv -a 1.33
```
This would re-encode movie.mkv and every episode of "television show" with a constant quality of 21 and an aspect ratio of 1.33:1 (4:3).

So here is what I have so far:
```

processArguments() {
    while getopts "ha:r:" optionName; do
        case "$optionName" in
        h) echo "Help is on the way." ;;
        a) aspect=$OPTARG;;
        r) res=$OPTARG;;
        [?]) echo "Both -a and -r require one argument"; exit 1;;
        esac
    done

    # Input file processing
    eval file=\$$OPTIND

    if [[ -z $file ]];
        then
        echo -e "${colorError}Error: Please enter a file name$colorEnd"
        exit 1
    fi
    if [ ! -f $file ]; then
        echo -e "${colorError}Error: File does not exist or is a directory$colorEnd"
        exit 1
    fi

    # Resolution processing
    if [ "$res" ]; then
        if [ "$aspect" ]; then
            echo -e "${colorWarning}Warning: You have selected both an aspect ratio and a resolution.  Defaulting to selected resolution.$colorEnd"
        fi

        x=`echo "$res" | sed "s/x[0-9]*$//"`
        y=`echo "$res" | sed "s/^[0-9]*x//"`

        if [[ `echo $res | grep -o "x" | wc -l | sed s/\ //g` -ne 1 ]] || ! [[ "$x" =~ ^[0-9]+$ ]] || ! [[ "$y" =~ ^[0-9]+$ ]] ; then
            echo -e "${colorError}Error: Malformed Resolution$colorEnd" >&2
            exit 1
        fi
    elif [ "$aspect" ]; then
        if ! [[ "$aspect" =~ ^[0-9]+([.][0-9]+)?$ ]]; then
            echo -e "${colorError}Error: Aspect ratio must be a floating point number$colorEnd" >&2
            exit 1
        fi

        divis=16
        x=640
        xFactor=`echo "$x / $divis" | bc`
        yFactor=`echo "$xFactor / $aspect" | bc -l`
        #echo "x: $xFactor y: $yFactor"
        yFactor=`printf "%.0f" $yFactor`
        y=$((yFactor * 16 ))
    else
        #user has made no selection
        echo -e "${colorWarning}Warning: No aspect ratio or resolution was specified.  Setting to default.$colorEnd"
    fi
}

```

So far this works alright but there are some specific limitations that are holding me back:
1) I can only encode one video at a time
2) I can't get non-option arguments that have spaces, even if they're escaped
3) I can't have option-arguments after the video filename
4) I'm having trouble with the aspect ratio based resolution selection in the math: if the unrounded y factor is supposed to be 22.5 it should round up, but it comes back as 22.4987987 and rounds down using "echo "$xFactor / $aspect" | bc -l", so is there a better more accurate way to do that math?

Also, just in general this seems like a lot of code to do some relatively simple stuff, and I wanted to know if maybe I was going about this the wrong way.  Is getopts the right option?  Is there a better way to round?  Any other style suggestions for a first time basher?

Thanks all so much,
Stella

---

### Post by Mizutsuki on 2009-08-19
Bump

---


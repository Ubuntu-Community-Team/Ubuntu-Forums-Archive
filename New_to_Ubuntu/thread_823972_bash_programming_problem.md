---
title: "bash programming problem"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by hasqual on 2008-06-09
I am pretty new to ubuntu and shell programming.  I am trying to add to my ".bashrc" file, a statement that causes a new fg and bg color for my xterm window each time I make a call.  

See problem code here:
```

XNUM=0
BGARRAY=(violet darkred chocolate4 lightGreen  cornsilk2)
FGARRAY=(gray24 grey90  grey80     darkorchid4 tomato4)
if [ read='xtm' ]
then
    alias xtm="xterm -ls -bg ${BGARRAY[$XNUM]} -fg ${FGARRAY[$XNUM]} &"
    let XNUM++
fi

```
Now I'm sure all you smart programmers know the problem already.  What I'm getting is the first xterm window opening in violet and gray24 as expected, but never getting the later colors.  I'm guessing each time I type "xtm" to initiate the xterm sequence the XNUM variable is reset to "0" or or something, and that 0 is the first element in an array?  Can someone point me in the right direction?  I couldn't figure out how to keep the variable from being erased, nor could I figure out how to make a system call to "$XNUM" (like echo and returning the answer) and add 1 to the result then pass this into the $XNUM variable in my bash file/xtm call.  Any help?  Thanks!

~Jack

---

### Post by HalPomeranz on 2008-06-09
What you're trying to do is never going to work the way you're currently going.  Your biggest problem is that updating $XNUM in a subshell is never going to affect the parent shell.

Put this in your .bashrc file instead:

```

export BGARRAY=(violet darkred chocolate4 lightGreen  cornsilk2)
export FGARRAY=(gray24 grey90  grey80     darkorchid4 tomato4)
export XNUMFILE=$HOME/.xnumaccum
function xtm {
        if [ ! -f $XNUMFILE ]; then
                num=0
        else
                num=`cat $XNUMFILE`
                num=$(( ($num + 1) % 5 ))
        fi
        rm -f $XNUMFILE
        echo $num >$XNUMFILE
        xterm -ls -bg ${BGARRAY[$num]} -fg ${FGARRAY[$num]} &
}

```

This moves your $XNUM value into a file in your home directory so that it can be accessed/updated from any shell you happen to run the xtm function from.

---

### Post by hasqual on 2008-06-09
That was absolutely money.  Thank you so much, it does exactly what I want it to.  I'll work on studying it to make sure I get it, thanks so much for the help it is really appreciated!

One followup question.  If I want the sequence to "reset" whenever I close the first xterm window (terminate the session) what change should I make?  

For instance, if I get on and type "xtm" twice, I'll get the violet, then the darkred backgrounds.  If I exit altogether and get back on and type "xtm" again, it picks up at the chocolate4 background.  Is there a way to have it reset and start again at the violet background?  I'm trying to read and understand, but I'm pretty new and it's going pretty slow haha.  Thanks again!

~Jack

---


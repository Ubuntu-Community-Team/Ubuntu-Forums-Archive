---
title: "Helping with piping to gnuplot"
date: 2009-04-26
forum: Programming Talk
---

### Post by Tony7682 on 2009-04-26
Hi,

I am a new here. I did read the FAQ. I had a specific question about piping data to GNU Plot as part of a bash script.

What I am doing is the following: cat'ing out the contents of an [mgen]("http://cs.itd.nrl.navy.mil/work/mgen/") log file, piping that to [trpr]("http://pf.itd.nrl.navy.mil/protools/trpr.html") (which processes the mgen results into gnuplot-readable format), and then piping that output to gnuplot.

Here is the bash script I am running:

```
for i in $(seq 1 180)
do
    sleep 10
    if [ `expr $i % 6` -ne 0 ]; then
        # show snapshot
        **cat $MGLOGFILE | trpr drec real auto X | gnuplot -noraise -persist**
        if [ -f $PLOTFILE ]; then
            rm -vf $PLOTFILE
        fi
    else
        # show cumulative results
        cat $MGLOGFILE | trpr drec auto X output $PLOTFILE && gnuplot -noraise -persist $PLOTFILE
    fi
done

```(I've tried piping [FONT=Courier New]tail -f[/FONT] output instead of [FONT=Courier New]cat[/FONT] output to trpr, but that would not work for some reason.)

The above seems to be working ok except for one thing: Each call to the cat | trpr | gnuplot line (bolded above) causes a new, separate gnuplot window to open. What I would like is for each successive call to that line to direct its output to the same gnuplot. That way, I don't have a new gnuplot window popping up every 10 seconds.

My workaround right now is to have a wrapper script that periodically closes any gnuplot windows. I'd rather avoid having to do that, though.

Anyone know how to keep continually writing (and rewriting) to one gnuplot window?

---

### Post by lensman3 on 2009-04-27
Try the program "tee" just before the gnuplot.  "tee" will let you see the pipe.

---

### Post by Tony7682 on 2009-04-27
Thank you for the suggestion about the "tee" program. I have never heard of it nor used it before.

Can you elaborate on what you meant by "using it just before gnuplot"?

I've tried this:
```
cat $MGLOGFILE | trpr drec real auto X | [COLOR=Red]**tee**[/COLOR] | gnuplot -noraise -persist
```But the behavior seems the same as it was before. Each successive call to that line causes another new gnuplot window to pop up.

---

### Post by Arndt on 2009-04-27
> **Tony7682 said:**
> Thank you for the suggestion about the "tee" program. I have never heard of it nor used it before.

Can you elaborate on what you meant by "using it just before gnuplot"?

I've tried this:
```
cat $MGLOGFILE | trpr drec real auto X | [COLOR=Red]**tee**[/COLOR] | gnuplot -noraise -persist
```But the behavior seems the same as it was before. Each successive call to that line causes another new gnuplot window to pop up.

This is perhaps an approximation of you want to do:

```
#! /bin/sh

for i in sin cos tan
do
    echo $i 1>&2
    echo "plot $i(x)"
    sleep 3
done | gnuplot -persist

```

I tried to use a named pipe, but didn't succeed, maybe there is a way. Also, it may be possible to keep terminal output on stdout, and choose another file descriptor to pass the gnuplot commands on.

---

### Post by Tony7682 on 2009-04-27
Awesome! That's it! Pipe the entire for loop into gnuplot! Thanks so much!!

```
for i in $(seq 1 180)
do
    sleep 10
    cat $MGLOGFILE | trpr drec real auto X
done | gnuplot -persist
```

---

### Post by tjoccam on 2009-10-23
Hi, I used these hints and they are very useful indeed, but I'm not quite there. I succeeded with an animation using pre-made files. My code snippet is:
( echo "set yrange [-5:5]"
  echo "plot sin(x)"
  sleep 1
  for j in 0 1 2 3 4 ; do
    for i in 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 ; do
       echo "plot \"plot$i\" using 1:2 with linespoints"
       sleep 0.15
    done
  done
) | gnuplot -persist 
with some plot files I prepared ahead of time. (Without the plot sin(x) it pauses and then spits out several plots.) What I really want is to pipe in the output of 1 program, which has its own internal pauses, giving me an animation. Embedding plot "-" or plot '-' does not seem to work. What am I missing? TIA, Larry

---

### Post by Arndt on 2009-10-25
> **tjoccam said:**
> Hi, I used these hints and they are very useful indeed, but I'm not quite there. I succeeded with an animation using pre-made files. My code snippet is:
( echo "set yrange [-5:5]"
  echo "plot sin(x)"
  sleep 1
  for j in 0 1 2 3 4 ; do
    for i in 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 ; do
       echo "plot \"plot$i\" using 1:2 with linespoints"
       sleep 0.15
    done
  done
) | gnuplot -persist 
with some plot files I prepared ahead of time. (Without the plot sin(x) it pauses and then spits out several plots.) What I really want is to pipe in the output of 1 program, which has its own internal pauses, giving me an animation. Embedding plot "-" or plot '-' does not seem to work. What am I missing? TIA, Larry

I'm not sure. Pipe I/O is buffered, which may be the reason for the pausing problems. If so, maybe using the program 'expect' to connect the two programs will work better.

---


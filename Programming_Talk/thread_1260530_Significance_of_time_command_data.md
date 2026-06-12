---
title: "Significance of time command data"
date: 2009-09-07
forum: Programming Talk
---

### Post by kaibob on 2009-09-07
Primarily as a learning experience, I wrote a Bash shell script that cycles through desktop windows with one window change for each execution of the script. The original version contained the following line, which uses awk to obtain the identity number of the window that has the focus and to add a needed zero:

```
focus=$(xprop -root _NET_ACTIVE_WINDOW | awk '{ sub(/0x/,"0x0"); print $NF}')
```

I then decided to replace this with bash:

```
focus=$(xprop -root _NET_ACTIVE_WINDOW)
focus=${focus##* }
focus=${focus/0x/0x0}
```

Finally, I ran some time command tests as shown below. I ran these tests with only two open windows--gnome-terminal and a leafpad text editor. The two shell scripts are named cycle-bash and cycle-awk.  

```
$ time for i in $(seq 100) ; do cycle-bash ; done
real	0m9.221s
user	0m0.876s
sys	0m1.320s

$ time for i in $(seq 100) ; do cycle-awk ; done
real	0m9.571s
user	0m1.064s
sys	0m1.456s

$ time for i in $(seq 100) ; do cycle-bash ; done
real	0m9.254s
user	0m0.916s
sys	0m1.180s

$ time for i in $(seq 100) ; do cycle-awk ; done
real	0m9.598s
user	0m1.020s
sys	0m1.460s

$ time for i in $(seq 100) ; do cycle-bash ; done
real	0m9.290s
user	0m0.884s
sys	0m1.252s

$ time for i in $(seq 100) ; do cycle-awk ; done
real	0m9.623s
user	0m1.140s
sys	0m1.404s
```

The difference in the real time data between the two shell script versions is about 3.5 percent. Is there some reason that this difference might be inaccurate or misleading? The reason I ask is that I have previously found awk-versions of other shell scripts to be faster than bash versions. Also, the thought occurred to me that any attempt to optimize shell scripts such as this are probably not worth the effort.

Thanks for the help.

---

### Post by jpkotta on 2009-09-07
The awk version has to exec an awk process, whereas the bash one doesn't.  But really, you're probably right to not worry about optimizing this.

---


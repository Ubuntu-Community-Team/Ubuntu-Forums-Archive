---
title: "Sed giving me invalid range end message"
date: 2009-02-17
forum: Programming Talk
---

### Post by forthekill on 2009-02-17
I am trying to replace occurrences of uppercase-lowercase pairs in a file with spaces, using [FONT="Courier New"]sed[/FONT] but it is not working.

For example, I want to find Rb or Ti or Am and replace them with spaces.

Using the command:

```
sed 's/[A-z]/ /g'
```

gives me an error:

```
sed: -e expression #1, char 11: Invalid range end
```

I don't understand what is wrong with that command. Can someone help?

I am using Ubuntu 8.10.

---

### Post by Yuzem on 2009-02-17
Try this:
```
sed 's/[a-z]/ /Ig'
```

---

### Post by Martin Witte on 2009-02-17
[A-z] is not a valid range hence the error, is this what you want?
```
martin@toshibap200:~$ cat testfile
Zs xx Cd vbnm zWqrety
martin@toshibap200:~$ sed 's/[A-Z][a-z]/  /g' testfile
   xx    vbnm z  rety
martin@toshibap200:~$
```

---

### Post by forthekill on 2009-02-18
Thanks a ton :)

---

### Post by zolero on 2011-06-09
Hi there.

I have a similar behavior with sed in bluesoleil linux package's postinstall script. There is the following:

```
files=`find /etc -name '[Ss]*[Hh]al' 2>/dev/null`

for file in $files; do
    basefile=`basename $file`;
    digit=`echo $basefile | [COLOR=Red]sed 's/[a-Z]//g'[/COLOR]`;
    if [ ! -z $digit ] && [ "$digit" != "" ];then
        while [ "$digit" -lt "99" ]
            do
...

```Now, for the red marked expression I get this in terminal:
```
root@bluestorm:/home/zolero/Ghernyo# dpkg -i *.deb
Selecting previously deselected package bluesoleil.
(Reading database ... 271543 files and directories currently installed.)
Unpacking bluesoleil (from bluesoleil_1.1.0.9-1zbstorm1_i386.deb) ...
Welcome to the BlueSoleil world!
Setting up bluesoleil (1.1.0.9-1zbstorm1) ...
Please reboot to use BlueSoleil!
[COLOR=Red]sed: -e expression #1, char 10: Invalid range end
sed: -e expression #1, char 10: Invalid range end
sed: -e expression #1, char 10: Invalid range end
sed: -e expression #1, char 10: Invalid range end[/COLOR]
Enjoy BlueSoleil![FONT=monospace]
[/FONT]root@bluestorm:/home/zolero/Ghernyo#
```I've googled a lot for this, and tried some other expression variants, but no luck. This crap annoys me and drives me crazy...  :mad:  What tha heck have to put there to solve it..  :?:  Please help me to turn this error message off. Thanks in advance.

---

### Post by geirha on 2011-06-10
[a-Z] will typically be valid in your locale, but not the C-locale, since in the C locale, all uppercase letters sort before lowercase letters. Better to just use [[:alpha:]] instead.

That script is badly written btw, so it's not surprising that it'll fail under "odd" circumstances. What is the script trying to do?

---

### Post by Yuzem on 2011-06-10
Try this:

```
files=`find /etc -name '[Ss]*[Hh]al' 2>/dev/null`

for file in $files; do
    basefile=`basename $file`;
    [COLOR="Red"]digit=${basefile//[a-z]};[/COLOR]
    if [ ! -z $digit ] && [ "$digit" != "" ];then
        while [ "$digit" -lt "99" ]
            do

```

That should replace both uppercase and lowercase letters.
You should also replace basename for:
```
basefile=${file##*/};
```

---

### Post by zolero on 2011-06-10
> **geirha said:**
> That script is badly written btw, so it's not surprising that it'll fail under "odd" circumstances. What is the script trying to do?

I'm not the author of this script... am just an editor of it, and the BlueSoleil Linux package (version 1.1.0.9 for Ubuntu 8.04.x LTS Hardy Heron. I will solve also the kernel dependency problem for the 1.3.1.5 version for Ubuntu 9.10 Karmic Koala to be useable on any running kernel version ;) if anyone is interested...) Original author is a gentleman named JiaDianlong, from IVT Corporation, who had built a so poor Ubuntu package, that I'm wondering where had he learnt Ubuntu and its packaging policy. Anyway, I wanted  to correct it for personal usage, and manually made all the repairs needed. Although package is ready, and works well, I want this message turned off.

The quoted part with the trouble **is a part of the package's postinstall script**, as I wrote earlier, and is supposed to find a suitable call sequence number for the "observer" boot initscript, in order to automate the BlueSoleil driver functionality at system startup.

```
# Find a suitable sequence number, which determines to call the "observer" boot-script.
# The number must be larger than the corresponding number of "hal" service, and - for
# better stability - it shouldn't occupied by any other boot service.

files=`find /etc -name '[Ss]*[Hh]al' 2>/dev/null`

for file in $files; do
    basefile=`basename $file`;
    digit=`echo $basefile | [COLOR=Red]sed 's/[a-Z]//g'[/COLOR]`;
    if [ ! -z $digit ] && [ "$digit" != "" ];then
        while [ "$digit" -lt "99" ]
            do
                digit=`expr $digit + 1`;
                substitute=`echo $basefile | sed -e "s/[0-9][0-9][a-Z]*/$digit/"`*
                if [ -z "`find /etc -name $substitute 2>/dev/null`" ];then
                    break;
                fi
            done
        break;
    fi
done

#update-rc.d observer defaults >/dev/null

if [ ! -z $digit ];then
    update-rc.d observer start $digit 2 3 4 5 . stop `expr 100 - $digit` 0 1 6 . >/dev/null
else
    update-rc.d observer defaults >/dev/null
fi
```This above is the entire section supposed to do that, with authors commenting note. Can anyone give me the correct answer to turning this message off, please? Thanks **geirha** for trying to help...

I will thank also to **Yuzem,** for trying to solve this, but following his advice I've got just this:
```
root@bluestorm:/home/zolero/Ghernyo# dpkg -i *.deb
Selecting previously deselected package bluesoleil.
(Reading database ... 271543 files and directories currently installed.)
Unpacking bluesoleil (from bluesoleil_1.1.0.9-1zbstorm1_i386.deb) ...
Welcome to the BlueSoleil world!
Setting up bluesoleil (1.1.0.9-1zbstorm1) ...
Please reboot to use BlueSoleil!
[COLOR=Red]/var/lib/dpkg/info/bluesoleil.postinst: line 99: [: S24: integer expression expected
expr: non-numeric argument
update-rc.d: error: expected NN after start
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults|multiuser [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
        -n: not really
        -f: force[/COLOR]
Enjoy BlueSoleil!

root@bluestorm:/home/zolero/Ghernyo#
```The output let me know that the sed expression must be an integer, as it is a further variable for the update-rc.d script, something like S24observer I guess... Any other tips...?

---

### Post by geirha on 2011-06-10
Oh dear, it's looking for files like /etc/rc2.d/S20hal. In order to give the script a lower start priority during boot (20+1 if it had found S20hal). Now apart from the backwards way of doing that, [Ubuntu no longer uses hal](http://en.wikipedia.org/wiki/HAL_(software)#Deprecated), so it won't find it...

I guess your best bet is to rewrite that init-script as an [upstart script](http://upstart.ubuntu.com/) that runs some time after udev.

---

### Post by zolero on 2011-06-10
Yes **geirha**, it looks for the hal daemon startup scripts, and yes, **it's a Hardy Heron machine**, that uses the hal (v0.5.11~rc2-1ubuntu8.3) daemon, even if newer versions don't use it anymore.

Now, since I don't want to upgrade my main home machine to - say Lucid, to be in sync with latest LTS release - something newer edition, I have to manage things to work well even on hal. Therefore I like to have a solution **for this** script if possible, please.

And I am not a retrograd, as one may suppose upon all above... The prove is that I chose the 1.1.0.9 version of BlueSoleil Linux for Hardy. Things are way different when we speak about my new Dell Inspiron laptop, where I run Lucid Lynx and - of course - there isn't hal anymore. So in the newest version of BlueSoleil Linux (1.3.1.5) I will adapt things upon newest situation requests. But my main machine remains Hardy Heron as for now. It runs my custom built kernel without even the littlest problem for 3 years now, is lightning fast, reliable, and boots up in a blink of eye (max. 35 secs from a cold start). I am convinced, that these reasons are enough to stay on Hardy Heron for now...  ;)

Thanks again **geirha**, but I need a solution **for this problem,** not for my machine OS upgrade, if you don't mind... Anyone else, please?

---

### Post by geirha on 2011-06-11
I see, somehow I got the idea you were trying to wedge in a Hardy-package on a newer system. Anyway, I took a look at how the hal-package does it, and this seems to be it:

```
# from debian/rules
DEB_DH_INSTALLINIT_ARGS := -- start 24 2 3 4 5 . stop 16 1 .

```

So just do something similar for that package, e.g.:
```

DEB_DH_INSTALLINIT_ARGS := -- start 25 2 3 4 5 . stop 15 1 .

```

Though I guess it depends on how much that package deviates from a typical deb package. So possibly you might have to run an update-rc.d line in that postinst script instead.

---


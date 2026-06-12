---
title: "Little bash script for new users - any thoughts?"
date: 2010-07-26
forum: Programming Talk
---

### Post by J V on 2010-07-26
Potential improvements:

[LIST]
[*]Bug-check
[/LIST]


```
#! /bin/bash

function apply {
$pdone=0
if [[ $1 =~ "xorg" ]]; then
setxkbmap -option terminate:ctrl_alt_bksp
#echo to stdout: echo "Set Xorg shortcut"

let pdone=$pdone+5
echo $pdone

fi
if [[ $1 =~ "hosts" ]]; then
wget -qO- http://www.mvps.org/winhelp2002/hosts.txt | sed -e 's/127\.0\.0\.1 *localhost//g' -e 's/127\.0\.0\.1/0\.0\.0\.0/g' | gksudo tee -a /etc/hosts

let pdone=$pdone+10
echo $pdone

fi
if [[ $1 =~ "extras" ]]; then
extras="ubuntu-restricted-extras"
fi
if [[ $1 =~ "pol" ]]; then
pol="playonlinux"
fi
if [[ $1 =~ "dvd" ]]; then
dvd="libdvdread4"
dvdread="gksudo /usr/share/doc/libdvdread4/install-css.sh"
fi

gconftool-2 --set --type bool /apps/update-notifier/auto_launch false &
gconftool-2 --set --type bool /desktop/gnome/interface/menus_have_icons true &
gconftool-2 --set --type string /desktop/gnome/interface/toolbar_style "icons" &

let pdone=$pdone+5
echo $pdone

gksudo apt-get update
echo 25
gksudo apt-get -y upgrade 
echo 50
gksudo apt-get -y install preload gimp p7zip-full simple-ccsm $dvd $extras $pol
echo 90

$dvdread
$confirmdvdread

echo 100
}

output=`zenity --title "" --print-column 3 --hide-column 3 --separator " " --width 740 --height 258 --text "Which items would you like to install" --list --checklist --column "" --column "" --column "" \
TRUE "Do you want to enable 'Control + Alt + Backspace' shortcut to quickly restart X in case of crash?" "xorg" \
TRUE "Do you want to block advertisements and potential malware with a hosts file?" "hosts" \
TRUE "Do you want to install flash, video and audio codecs, and other propreitary formats?" "extras" \
TRUE "Do you want to install PlayOnLinux to help you run windows programs on Linux?" "pol" \
TRUE "Do you want to install the CSS decoder to play DVDs? WARNING: Illegal in US (Though rarely enforced)" "dvd"`

if [[ $? == 0 ]]; then
apply $output | zenity --title "Working..." --progress --pulsate
else
echo "Cancelled, exitting"
exit 1
fi
```

---

### Post by KdotJ on 2010-07-26
I like it, and I like the idea. Though I think one of your main problems will be getting new users to run a, to them "random" and perhaps untrusted,  script

---

### Post by J V on 2010-07-27
Of course, perhaps use zenity to make it look nicer, add a lot of comments?

How can I add variables to variables? Something like this:

```
if true; then
var1 = "${var1}texthere"
```My problem is that when the entire command has to be between quotes for to pass it to the function it won't assign the variable later...

```
com1="varres=\" ubuntu-restricted-extras\""

$com1 # Error

echo $varres # No response
```

---

### Post by VH-BIL on 2010-07-27
You could use zenity to provide a GUI yes no dialog.

---

### Post by ghostdog74 on 2010-07-27
> **J V said:**
> 


```
#! /bin/bash
...
    if [[ -n "`echo "$input" | grep -i [ny]`" ]]; then
        if [[ -n "`echo "$input" | grep -i y`" ]] && [[ -z "`echo "$input" | grep -i n`" ]]; then
            $2
        fi
...
}
```

you can use case/esac here

```

case "$input" in
  [yY] )  echo "do something" ;;
  [nN] )  echo "do something" ;;
  *)  echo "else" ;;
esac

```

No need to call external grep command.

---

### Post by J V on 2010-07-27
@Ghost: I suppose that's more economical, but the code with zenity is much simpler: ```
function yesno {
    zenity --question --title="" --text="$1"
    if [[ $? == "0" ]]; then
        $2
    echo "Ran command: $2"
    fi
}
```
@BIL: Yes I have a script that does that but I need the command in the "yesno" function to create a string to append to the sudo apt-get install command... Only it won't work (See last code block)

---

### Post by VH-BIL on 2010-07-27
if it is just for sudo apt-get try
```
function yesno {
    zenity --question --title="" --text="$1"
    if [[ $? == "0" ]]; then
        gksudo apt-get install $2
    echo "Ran command: gksudo apt-get install $2"
    fi
}
```

and just pass the packages to the function. I have not tested this but I am pretty sure this will work.

---

### Post by J V on 2010-07-27
As am I, but this means the user will have to wait minutes between dialogues - I was hoping to concatenate the packages onto the end of an apt-get install command and use a zenity progress window to show the user something was happening: The only time the user has to wait something is actually being done...

---

### Post by VH-BIL on 2010-07-27
I don't understand, you can still do this with some script changes.

---

### Post by J V on 2010-07-28
Ok, I think I can workaround with the let command...

I would like to know how to get the text from a zenity --text window though, I can't seem to get the length of the $? string so I could pull it's substring...

---

### Post by VH-BIL on 2010-07-28
try getting rid of the yes no dialog and using a zenity checkbox option dialog.

check out:
[http://ubuntuforums.org/showthread.php?t=709735](http://ubuntuforums.org/showthread.php?t=709735)

---

### Post by J V on 2010-07-28
That was my original idea, only I forgot you could do it with zenity :)

Any way to make multiple line descriptions (Or disable/hide the checkbox on certain lines to give that effect)

How do I transfer the output (Simple id column hidden from user) into a pre-determined true/false list, or should I search the output in every if statement

---

### Post by VH-BIL on 2010-07-29
I have attached a C# application I did for you that will do what you want. It uses a config file that you can put all the jobs in. All of the jobs are done when all of the questions have been asked. All of the packages are downloaded in one apt-get like you wanted as well.

I have included the monodevelop source code in case you want to edit the user interface or code.

The binaries are in JVSetup/bin/Debug/

Here is an example config file:
```
JVSetup
Echo Hello1~N~echo Hello1
Add Package test1~Y~test1
Echo Hello2~N~echo Hello2
Echo Hello3~N~echo Hello3
Add Package test2~Y~test2
Add Package test3~Y~test3
Echo Hello4~N~echo Hello4
```

The first line is the applications title so you can change it easily.

The separator is the ~ character.

The jobs are stuctured like this:
job question~is package~action to perform or name of package

example of job:
Echo Hello To Term~N~echo hello

notice there is a N in the middle that tells the application that is an external application to run and not package to download.

example of package:
Download xzip~Y~xzip

The question will be "Download xzip" and because Y is in the middle xzip will be added to the list of packages to be downloaded.

---

### Post by J V on 2010-07-29
Well I don't want to add something not already in buntu, and they're trying to stay away from mono apps cause of potential ms interference... (Hence disappearance of fspot and tomboy soon)

could you perhaps create a case statement that searches a string for a substring?

something like this:
```
case $1 in: #How to make it regex search this?
"x")
setxkbmap -option terminate:ctrl_alt_bksp
;;
"hosts")
wget -qO- http://www.mvps.org/winhelp2002/hosts.txt | sudo tee -a /etc/hosts # use sed
;;
"extras")
extras="ubuntu-restricted-extras"
;;
"pol")
pol="playonlinux"
;;
"dvd")
dvd="libdvdread4"
dvdread="gksudo /usr/share/doc/libdvdread4/install-css.sh"
;;
```

---

### Post by VH-BIL on 2010-07-29
I just tried to search every where that Ubuntu are removing mono applications and can only see they are adding more not removing. Mono is a Novel influence.

The only thing I can see that was debated was the removal of the System.Windows.Forms library from a default install (I didn't use that library in that application, I used GTK) and the reason was childish as if coming from a complete moron! The argument was:
> System.Windows.Forms are not included by default, and are rarely used in Free applications anyway (because WinForms looks like ***, amongst other things).

The argument to me as a programmer is annoying as mono (which is a Novel product not Microsoft) can only improve the state of Linux by enabling Programmers to easily create applications that run on Windows, MacOSX, and Linux. There are now even mono enviroments for iPhone and Android! so applications can be easily ported to them as well!

Why don't they argue to remove SAMBA from Linux as Microsoft is actually contributing source code to the project? It is because SAMBA improves Linux and enables Linux to connect to many network devices that use that protocol.

I just looked at blogs on GNOME3 and they are not looking at changing TomBoy Notes from mono.

The script you are creating is something that is not already in Ubuntu so I don't see how a binary application is any different from that.

It is up to you if decide to still bash script it but it is easier to create an application. If you don't like mono use python, or hard code the config file into the application I made for you so you are only distributing 1 file instead of 2 if that was the problem.

---

### Post by J V on 2010-07-29
Well, that's what I heard... ( [http://www.tectonic.co.za/2010/06/ubuntu-one-step-closer-to-dropping-mono/](http://www.tectonic.co.za/2010/06/ubuntu-one-step-closer-to-dropping-mono/) says 10.10 drops fspot and tomboy is the last mono app in it by default, also, gnome doesn't decide what apps go in individual distros, and samba doesn't use any MS code, except what they put in it themselves, and is protected by EU reverse-engineering law)

Anyway, a nice short little bash script means it's instantly open source and compact, its more a quick download/run thing for newbies or if you go around installing ubuntu on peoples machines... Plus, if I were to use python it would get much more complex...

Using zenity works great too, all I really need now is to figure out how to take the output from zenity and apply some flow control...

Edit: Latest version on #1

---

### Post by phrostbyte on 2010-07-29
You can save state inside of variables. You could make one function that creates the variable based on user input and another that consumes it. This will allow you to ask all the questions at the start.

---

### Post by J V on 2010-07-30
Ok, latest (And hopefully last) problem, I want to pass the output to a zenity progress window so I can demonstrate this is going somewhere, but I also want to echo some things to stdout, how do I split this up?

Everything I echo is going to zenity by default, how do I make certain echoes go to stdout instead...

---

### Post by J V on 2010-08-03
Decided to work on the hosts file for now:

```
wget -qO- http://www.mvps.org/winhelp2002/hosts.txt | sed -e 's/127\.0\.0\.1 *localhost//g' -e 's/127\.0\.0\.1/0\.0\.0\.0/g' | gksudo tee -a /etc/hosts
```

As you can see, it downloads a modified hosts file, removes the localhost line, turns all the 127.0.0.1 into 0.0.0.0 (Because they work faster) and appends it to the hosts file...

Problem: I need it to only replace the second instance of localhost (The first one is in the comment description)
Question: Why does * work in the regex but {1,} and + don't?

---


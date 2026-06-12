---
title: "&quot;mv&quot; and &quot;locate&quot; commands in bash"
date: 2011-10-30
forum: New to Ubuntu
---

### Post by Ms. Daisy on 2011-10-30
I've been playing with bash as I read an Ubuntu user's manual.  A command has perplexed me, I'm hoping someone can clear it up.  Using the following code while staying in the ~ directory```
locate daisyCartoon.jpg
```I discover that this file is stored in the Pictures folder.  I want to move it to the desktop, so I type in```
mv /home/mycomputer/Pictures/daisyCartoon.jpg Desktop/
``` Now I want to locate the same file, which we know is actually on the desktop.  Proof: I can see the icon in the GUI and bash didn't complain with the mv command.  So I type in ```
locate daisyCartoon.jpg
```And bash tells me that it's located here:```
/home/mycomputer/Pictures/daisyCartoon.jpg
```WHAT?!? Why isn't it in Desktop?  I thought that perhaps I needed to exit the terminal & open a new one, but I got the same result.  If I want to move the jpg back to the Pictures folder, I have to type in```
mv Desktop/daisyCartoon.jpg /home/mycomputer/Pictures/
``` bash didn't complain and I could see the icon pop back into the Pictures folder in the GUI.  So what gives? What am I not understanding?

---

### Post by wojox on 2011-10-30
Move it back to the Desktop and then run 

```
sudo updatedb
```

Try locate again. :P

---

### Post by Ms. Daisy on 2011-10-30
> **wojox said:**
> Move it back to the Desktop and then run 

```
sudo updatedb
```Try locate again. :PSo should I update the database every time I use locate?

---

### Post by wojox on 2011-10-30
I'm not on Linux right now but I believe there is a cron script that runs every hour that does that.

---

### Post by Ms. Daisy on 2011-10-30
> **wojox said:**
> I'm not on Linux right now but I believe there is a cron script that runs every hour that does that.Aha.  So it's necessary to either run updatedb or to create/use a script in crontab -e whenever I use the locate command?

---

### Post by enkay009 on 2011-10-30
The thing about locate is that it gives you a speedy lookup but it can do this because it doesn't actually search the filesystem but rather a database.

Now you can do as other people have suggested and run a cron that updates this database at whatever interval makes sense to you... or

You can use **find.**

Find is very useful UNIX command. And even more useful when you use the **-exec** option. But I digress.

Here's a simple example you can use to find that jpg from within your home directory (~).

```
find ~ -type f -name 'daisyCartoon.jpg'
```

What this does is it search your home directory recursively (*~*) for all files (*-type f*) with the name daisyCartoon.jpg (*-name 'daisyCartoon.jpg*). 

BTW, have fun learning bash. :)

---

### Post by WasMeHere on 2011-10-30
> **enkay009 said:**
> the thing about locate is that it gives you a speedy lookup but it can do this because it doesn't actually search the filesystem but rather a database.

Now you can do as other people have suggested and run a cron that updates this database at whatever interval makes sense to you... Or

you can use **find.**

find is very useful unix command. And even more useful when you use the **-exec** option. But i digress.

Here's a simple example you can use to find that jpg from within your home directory (~).

```
find ~ -type f -name 'daisycartoon.jpg'
```

what this does is it search your home directory recursively (*~*) for all files (*-type f*) with the name daisycartoon.jpg (*-name 'daisycartoon.jpg*). 

Btw, have fun learning bash. :)

+1

---

### Post by JKyleOKC on 2011-10-30
> **Ms. Daisy said:**
> Aha.  So it's necessary to either run updatedb or to create/use a script in crontab -e whenever I use the locate command?No, only after you move something to a new location. The "locate" command uses a database that's normally updated just once a day, usually around 7 a.m., by a cron job. The idea is to make sure that all changes are up to date at the start of the day. It does not get updated automatically again until the next time that cron job runs, but you can update it manually if you make a change that needs to be there.

Unless you actually make heavy use of "locate" there's no real need to update its database manually, though. For example, in the 10 years I've been using Linux I can't recall having used "locate" even once!

---

### Post by Ms. Daisy on 2011-10-30
Thank you all.  It makes perfect sense now.  Now I have some new toys to play with: cron, find and -exec
:)

---

### Post by Slim Odds on 2011-10-30
locate was never intended to be for files that might move. It's really meant for executable (program) files, static libraries and stuff like that.

I believe that the cron job that runs updatedb runs one a day. Updating the database on any system is a bit time consuming.

I would consider learning how to use 'find' a must.

---

### Post by JKyleOKC on 2011-10-31
Absolutely! While I can't remember ever having used "locate" I do use "find" several times a week, whenever I'm unable to remember (or never learned) the exact location of a file. Here are a couple of tips for getting started with it:

First, run it as "sudo find" whenever you're searching the entire disk; otherwise you'll get quite a few "access denied" error messages and it may stop prematurely.

Second, get acquainted with all its options by reading the output of "man find" because there are many of them. The command that I use most often looks like this: ```
sudo find / -iname *.txt
```That will find all files whose names end in "txt" without running into case sensitivity, and output a list of their full paths. It doesn't work exactly like "locate" but it solves lots of problems.

If you're more comfortable reading from a GUI than from the command line, get familiar with the "xman" program. I've installed it as a launcher so that I can use it at any time; it will display the "man" pages for any program on your system that has one. Its interface takes a bit of getting used to but once you do, it's simple to search for the command you want to know about, without interrupting your terminal session to look things up.

Here's the launcher command I use for xman; it puts the display in the top right corner of my 1440x900 display:```
xman -notopbox -pagesize 829x814-0-6
```It opens on its own help page; left-clicking the mouse in the scroll bar will advance by a page, and right-clicking will move back by a page. Happy reading!

---

### Post by Paddy Landau on 2011-10-31
> **JKyleOKC said:**
> First, run it as "sudo find" whenever you're searching the entire disk...
But don't use sudo if you're just looking for your own files.

> **JKyleOKC said:**
> ```
sudo find / -iname *.txt
```
Get into the habit of putting quotes around the name:
```
sudo find / -iname [COLOR=Red]'[/COLOR]*.txt[COLOR=Red]'[/COLOR]
```Without the quotes, you can get restricted results (depending on the circumstances).

---

### Post by Ms. Daisy on 2011-10-31
Excellent information from everyone- thanks much.  About the quotes- I read that bash interprets spaces in a file name as an indication that arguments or options follow.  Quotes around the file name will prevent that. So it sounds like good practice anyway to employ quotes around file names. Can you use both single or double quotes as long as you open & close with the same type?

---

### Post by Paddy Landau on 2011-10-31
> **Ms. Daisy said:**
> Can you use both single or double quotes as long as you open & close with the same type?

[LIST]
[*] Single quotes: This uses the contents exactly as is. If you wish to include a single quote within a single quote, it's a bit complicated:
```
echo 'It'\''s a nice day'   *# Result: It's a nice day*
```
[/LIST]

[LIST]
[*] Double quotes: This uses the contents as given, but it will interpret any parameters. A parameter starts with $ and is followed by a pair of curly braces {}. (Under some circumstances, you can do without the braces, but it's good practice always to include them.)
```
echo "I am ${USER}"    *# Result: I am paddy*
```
[/LIST]
Here are some examples to illustrate the difference between the quote marks. Commands are in [COLOR=Blue]blue[/COLOR] and the results in **bold**.

```
[COLOR=Blue]echo '$( date | cut --fields=2 --delimiter=" " )'[/COLOR]
**$( date | cut --fields=2 --delimiter=" " )**

[COLOR=Blue]echo "$( date | cut --fields=2 --delimiter=' ' )"[/COLOR]
**Oct**

[COLOR=Blue]SPACER='A B    C      D        E'[/COLOR]    *# Note the spaces*
[COLOR=Blue]echo '${SPACER}'[/COLOR]
**${SPACER}**
[COLOR=Blue]echo "${SPACER}"[/COLOR]
**A B    C      D        E**
[COLOR=Blue]echo ${SPACER}[/COLOR]
**A B C D E**

[COLOR=Blue]for ITEM in '${SPACER}'; do echo "${ITEM}"; done[/COLOR]
**${SPACER}**
[COLOR=Blue]for ITEM in "${SPACER}"; do echo "${ITEM}"; done[/COLOR]
**A B    C      D        E**
[COLOR=Blue]for ITEM in ${SPACER}; do echo "${ITEM}"; done[/COLOR]
[B]A
B
C
D
E[/B]

*# And now for the exception: ANSI-C Quoting.*
[COLOR=Blue]echo Line 1\nLine 2[/COLOR]      *# Backslash means "use the following character without interpretation".*
**Line 1nLine 2**
[COLOR=Blue]echo 'Line 1\nLine 2'[/COLOR]    *# But in quotes, the backslash is just a backslash.*
**Line 1\nLine 2**
[COLOR=Blue]echo $'Line 1\nLine 2'[/COLOR]   *# The $ sign with single quotes makes a difference. \n = new line*
[B]Line 1
Line 2[/B]
[COLOR=Blue]echo "Line 1\nLine 2"[/COLOR]    *# In quotes, the backslash is just a backslash.*
**Line 1\nLine 2**
[COLOR=Blue]echo $"Line 1\nLine 2"[/COLOR]   *# The $ sign means nothing with double-quotes.*
**Line 1\nLine 2**
```To find out more about parameter expansion, see the Bash manual (open the terminal and enter *man bash*). Search for *EXPANSION*; also search for *Special Parameters*. For ANSI_C quoting, search for *QUOTING*.

---

### Post by JKyleOKC on 2011-10-31
> **Paddy Landau said:**
> But don't use sudo if you're just looking for your own files.

Get into the habit of putting quotes around the name:
It doesn't hurt, though, to use sudo with find at any time, so long as you don't invoke its "-exec" option. Even if searching only for your own files, if you start from the root of the file system (find \ rather than find ~) you may still get access denied messages since some directories are readable only by the root user.

Using double quotes around file names, especially if they use wild cards as I did in the example, is a very good idea -- although I usually forget to do it, until an error message or lack of any result brings me to my senses! Thanks, Paddy.

---

### Post by Paddy Landau on 2011-10-31
> **JKyleOKC said:**
> It doesn't hurt, though, to use sudo with find at any time...
This is not good practice. You should get into the habit of using [FONT=Fixedsys]sudo[/FONT] only when you specifically know you need it. Otherwise, habit will become your enemy when one day you intend to (say) *[FONT=Fixedsys]find ... -delete[/FONT]* and end up doing *[FONT=Fixedsys]sudo find ... -delete[/FONT]*. I know I've made mistakes that would have been horrendous had I used [FONT=Fixedsys]sudo[/FONT].

Another useful option to use with [FONT=Fixedsys]find[/FONT], particularly in scripts or when using potentially destructive options (such as [FONT=Fixedsys]-delete[/FONT] and [FONT=Fixedsys]-exec[/FONT]) is [FONT=Fixedsys]-xdev[/FONT]. If you are using [FONT=Fixedsys]-xdev[/FONT], and you are searching from root, and your [FONT=Fixedsys]/home[/FONT] is on a separate partition, you will need to specify both root and [FONT=Fixedsys]/home[/FONT]:
```
find [COLOR=DarkRed]/ /home[/COLOR] -xdev ...
```

---

### Post by JKyleOKC on 2011-10-31
Perhaps the difference in our attitudes about this is because I never use any option to "find" that will do anything other than output data to "stdout" for me to use. Here's an example of the point I was trying to make:```

**jk@mehitabel:~$ find / -iname "*.txt"**
[COLOR="Red"]find: `/tmp/orbit-gdm': Permission denied
find: `/tmp/orbit-root': Permission denied
[/COLOR]find: `/net/ad.doubleclick.net/home/jk/Public': No such file or directory
find: `/net/ad.doubleclick.net/home/ftp/private': No such file or directory
find: `/net/ad.doubleclick.net/home/ftp/incoming': No such file or directory
find: `/net/mehitabel/home/jk/Public': No such file or directory
find: `/net/mehitabel/home/ftp/private': No such file or directory
find: `/net/mehitabel/home/ftp/incoming': No such file or directory
find: `/net/dj650': No such file or directory
find: `/net/datasave': No such file or directory
find: `/net/ttax': No such file or directory
find: `/net/winxp-1': No such file or directory
find: `/net/delphi': No such file or directory
find: `/net/eagle': No such file or directory
**jk@mehitabel:~$ sudo find / -iname "*.txt"**
[sudo] password for jk: 
find: `/net/ad.doubleclick.net/home/jk/Public': No such file or directory
find: `/net/ad.doubleclick.net/home/ftp/private': No such file or directory
find: `/net/ad.doubleclick.net/home/ftp/incoming': No such file or directory
find: `/net/mehitabel/home/jk/Public': No such file or directory
find: `/net/mehitabel/home/ftp/private': No such file or directory
find: `/net/mehitabel/home/ftp/incoming': No such file or directory
find: `/net/dj650': No such file or directory
find: `/net/datasave': No such file or directory
find: `/net/ttax': No such file or directory
find: `/net/winxp-1': No such file or directory
find: `/net/delphi': No such file or directory
find: `/net/eagle': No such file or directory
[COLOR="Lime"]/net/localhost/home/jk/Public/envdata.txt
/net/localhost/home/jk/Public/exp.txt
/net/localhost/home/jk/Public/printer.txt
/net/localhost/home/jk/Public/route.txt
/net/localhost/home/ftp/incoming/old/adam_vernon_info.txt
[/COLOR]jk@mehitabel:~$ 

```Note the two lines in red when I did not use "sudo" and the five lines in green when I did (all five of which are my own files, but were not found until I used "sudo" on the search; I have no idea why not, though).

I agree that sudo should never be used unless necessary, but feel that searching the entire filesystem starting with "/" is a case where it's required to get expected results.

We may be getting too far from the "absolute beginner" level with this discussion, but I think it's important to help beginners deal with permission problems! I don't think we're really that far apart in our recommendations -- it's just a matter of "always remember to never say never" (which of course contradicts itself not once but twice in the same sentence).

---

### Post by Ms. Daisy on 2011-10-31
> **JKyleOKC said:**
> We may be getting too far from the "absolute beginner" level with this discussion, but I think it's important to help beginners deal with permission problems! I don't think we're really that far apart in our recommendations -- it's just a matter of "always remember to never say never" (which of course contradicts itself not once but twice in the same sentence).Just for the record, this particular beginner loves to hear such discussions.  It reveals stuff that would have taken me a year to discover on my own.  So please, continue the banter!

---

### Post by garyed on 2011-10-31
> **JKyleOKC said:**
> ```

**jk@mehitabel:~$ find / -iname "*.txt"**
[COLOR="Red"]find: `/tmp/orbit-gdm': Permission denied
find: `/tmp/orbit-root': Permission denied
[/COLOR]find: `/net/ad.doubleclick.net/home/jk/Public': No such file or directory
find: `/net/ad.doubleclick.net/home/ftp/private': No such file or directory
find: `/net/ad.doubleclick.net/home/ftp/incoming': No such file or directory
find: `/net/mehitabel/home/jk/Public': No such file or directory
find: `/net/mehitabel/home/ftp/private': No such file or directory
find: `/net/mehitabel/home/ftp/incoming': No such file or directory
find: `/net/dj650': No such file or directory
find: `/net/datasave': No such file or directory
find: `/net/ttax': No such file or directory
find: `/net/winxp-1': No such file or directory
find: `/net/delphi': No such file or directory
find: `/net/eagle': No such file or directory
**jk@mehitabel:~$ sudo find / -iname "*.txt"**
[sudo] password for jk: 
find: `/net/ad.doubleclick.net/home/jk/Public': No such file or directory
find: `/net/ad.doubleclick.net/home/ftp/private': No such file or directory
find: `/net/ad.doubleclick.net/home/ftp/incoming': No such file or directory
find: `/net/mehitabel/home/jk/Public': No such file or directory
find: `/net/mehitabel/home/ftp/private': No such file or directory
find: `/net/mehitabel/home/ftp/incoming': No such file or directory
find: `/net/dj650': No such file or directory
find: `/net/datasave': No such file or directory
find: `/net/ttax': No such file or directory
find: `/net/winxp-1': No such file or directory
find: `/net/delphi': No such file or directory
find: `/net/eagle': No such file or directory
[COLOR="Lime"]/net/localhost/home/jk/Public/envdata.txt
/net/localhost/home/jk/Public/exp.txt
/net/localhost/home/jk/Public/printer.txt
/net/localhost/home/jk/Public/route.txt
/net/localhost/home/ftp/incoming/old/adam_vernon_info.txt
[/COLOR]jk@mehitabel:~$ 

```.

I'd sure like to know why you're getting " No such file or directory" output from the find command too.
 Can anyone explain that?

---

### Post by Telengard C64 on 2011-10-31
> **Ms. Daisy said:**
> Just for the record, this particular beginner loves to hear such discussions.  It reveals stuff that would have taken me a year to discover on my own.  So please, continue the banter!

You may also want to consult the full documentation for GNU Findutils. It covers **locate**, **find**, **updatedb** and **xargs** in great detail.

[http://www.gnu.org/software/findutils/manual/find.html](http://www.gnu.org/software/findutils/manual/find.html)

---

### Post by JKyleOKC on 2011-10-31
> **garyed said:**
> I'd sure like to know why you're getting " No such file or directory" output from the find command too.
 Can anyone explain that?That entire /net directory is associated with my installation of automount for NFS, and while its sub-directories do exist, themselves, they have no content until the automount daemon mounts the associated system. However I'm at a loss as to why that "ad.doubleclick.net" subdirectory exists, because that's certainly not anything listed in my automount configuration (at least, not put there by me, but it might be the result of some attempt by a browser to get there).

I just took a look at it through the Thunar file manager, and of course that mounted something via automount. What it mounted was my separate /home partition! I think I need to review my automount configuration files rather carefully!!!

Later: Just did that but see nothing amiss there. Hopefully someone else will chime in with some hints. The docs I've been able to find regarding automounting are not at all clear, and most of the examples I found when setting it up failed to work at all...

---

### Post by Paddy Landau on 2011-11-01
> **JKyleOKC said:**
> Perhaps the difference in our attitudes about this is because I never use any option to "find" that will do anything other than output data to "stdout" for me to use. Here's an example of the point I was trying to make:...
In this case, yes, you do need to use sudo because you are searching from a folder owned by someone other than yourself. As I said, don't use sudo *unless you need to*. Provided that your command is correct, you can suppress error messages as follows:```
sudo find / -iname "*.txt" 2>/dev/null
```It makes it easier to read.

> **JKyleOKC said:**
> ... the five lines in green when I did (all five of which are my own files,  but were not found until I used "sudo" on the search; I have no idea why  not, though).
Look at the permissions for each of [FONT=Fixedsys]/net[/FONT], [FONT=Fixedsys]/net/localhost[/FONT], [FONT=Fixedsys]/net/localhost/home[/FONT], etc. I suspect that one of them has no read- or execute-access to you.

---

### Post by JKyleOKC on 2011-11-01
> **Paddy Landau said:**
> Look at the permissions for each of [FONT=Fixedsys]/net[/FONT], [FONT=Fixedsys]/net/localhost[/FONT], [FONT=Fixedsys]/net/localhost/home[/FONT], etc. I suspect that one of them has no read- or execute-access to you.One would certainly think so, but that wasn't the case when I checked. Of course, automount is a bit of magic behind the scenes anyway and I know no way of telling what it's really doing. Any reference to the /net directory or any of its subdirectories tends to change the content, and I know of no way to tell how /find is referencing them. However here's what I see:```
jk@mehitabel:~$ ls -l /net
total 4
drwxr-xr-x 14 root root    0 2011-09-29 13:17 ./
drwxr-xr-x 25 root root 4096 2011-09-29 13:15 ../
dr-xr-xr-x  2 root root    0 2011-10-31 21:34 ad.doubleclick.net/
dr-xr-xr-x  2 root root    0 2011-09-29 13:17 datasave/
dr-xr-xr-x  2 root root    0 2011-09-29 13:17 delphi/
dr-xr-xr-x  2 root root    0 2011-09-29 13:17 dj650/
[COLOR="Red"]dr-xr-xr-x  2 root root    0 2011-09-29 13:17 eagle/
dr-xr-xr-x  2 root root    0 2011-10-31 16:57 localhost/
dr-xr-xr-x  2 root root    0 2011-10-31 16:41 mehitabel/
dr-xr-xr-x  2 root root    0 2011-09-29 13:17 neon/[/COLOR]
dr-xr-xr-x  2 root root    0 2011-09-29 13:17 publisher/
dr-xr-xr-x  2 root root    0 2011-09-29 13:17 ttax/
dr-xr-xr-x  2 root root    0 2011-09-29 13:17 winxp-1/
[COLOR="Red"]dr-xr-xr-x  2 root root    0 2011-09-29 13:17 xubuntu/[/COLOR]
jk@mehitabel:~$ 

```This shows both read and list permissions for each folder, even for its owner. Except for the one involving doubleclick, and localhost, these are all remote machines; those in red above are actual boxes and the rest are virtual machines. The "neon" and "eagle" systems are powered down, while all of the VMs except for "winxp-1" are in "saved" state and so are offline and not available.

Come to think of it, that explains the error messages! The automount daemon attempted to mount the system but it was not available to be mounted.

Sometimes I'm a bit dense, especially about things that in retrospect are obvious. That's one reason I welcome error messages most of the time -- they let me know when I'm on a wrong track!

---

### Post by nothingspecial on 2011-11-01
One thing is for sure.

Make sure you understand exactly what the command is going to do before you run it.

It is very easy to break your system with find if you make a mistake, especially with sudo.

---

### Post by Telengard C64 on 2011-11-01
> **nothingspecial said:**
> Make sure you understand exactly what the command is going to do before you run it.

+1
The manpages and GNU documentation were already pointed out.

> It is very easy to break your system with find if you make a mistake, especially with sudo.

Well yes, but the same can be said of any command run as root. You can break a system with any any command that writes to disk. For example, a redirected **echo** can destroy system files if run in a root shell.

---

### Post by Ms. Daisy on 2011-11-01
> **nothingspecial said:**
> It is very easy to break your system with find if you make a mistake, especially with sudo.> **Telengard C64 said:**
> You can break a system with any any command that writes to disk. For example, a redirected **echo** can destroy system files if run in a root shell.So would it be prudent to run terminal in a virtual box or sandbox when playing around with bash? Can that even be done? Or maybe there's some sort of test mode, where bash will tell you what will happen if you execute a command but without actually executing the command?  I've seen that feature on some software, don't know if it extends to terminal by itself.  Certainly I'm not the first person that needs to be saved from themselves in bash.

---

### Post by Telengard C64 on 2011-11-01
> **Ms. Daisy said:**
> So would it be prudent to run terminal in a virtual box or sandbox when playing around with bash? Can that even be done?

Yes, of course. I experimented with Linux (and Bash) in virtual machines for years before I committed to running it full time on my everyday machine.

> Or maybe there's some sort of test mode, where bash will tell you what will happen if you execute a command but without actually executing the command?  I've seen that feature on some software, don't know if it extends to terminal by itself.

Umm ... there is something called a *restricted shell*, but I don't know exactly what it is intended for.

> Certainly I'm not the first person that needs to be saved from themselves in bash.

Then please heed the most prudent advice I can think of. Before performing any action entailing risk of data or system, [please ensure you have reliable backups](http://blog.wisefaq.com/2010/01/05/backups-with-the-3-2-1-rule/).

---

### Post by Slim Odds on 2011-11-01
> **Ms. Daisy said:**
> So would it be prudent to run terminal in a virtual box or sandbox when playing around with bash? Can that even be done? Or maybe there's some sort of test mode, where bash will tell you what will happen if you execute a command but without actually executing the command?  I've seen that feature on some software, don't know if it extends to terminal by itself.  Certainly I'm not the first person that needs to be saved from themselves in bash.

Experimenting in the VM is an **excellent **idea. The best part is that you can make _snapshots _so that if you do something really bad you can go back to an earlier point in time.

---

### Post by Telengard C64 on 2011-11-01
> **Slim Odds said:**
> The best part is that you can make _snapshots _so that if you do something really bad you can go back to an earlier point in time.

Indeed! Another major advantage of VMs is that you can make full system backups by simply copying a single disk image file to external media.

---

### Post by Ms. Daisy on 2011-11-01
OK, so it sounds like you have to completely create a new OS in a VM.  It's not possible to just run terminal in a jail or sandbox, or to run it in "demo" or "test" mode. True?

---

### Post by Telengard C64 on 2011-11-01
> **Ms. Daisy said:**
> It's not possible to just run terminal in a jail or sandbox, or to run it in "demo" or "test" mode. True?

I'm sure one or more of those things must be possible, but I can't offer any advice as to how.

---

### Post by JKyleOKC on 2011-11-01
> **Ms. Daisy said:**
> OK, so it sounds like you have to completely create a new OS in a VM.  It's not possible to just run terminal in a jail or sandbox, or to run it in "demo" or "test" mode. True?That's correct, but it's not hard to do. First, install the VirtualBox program using Synaptic (or download it from the Oracle site at [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads) which has a link to the most current release, customized for Ubuntu users; be sure to also download the Extension Pack so that you can use USB devices). The first time you run it after doing the installation, it will launch a wizard that guides you through the creation of the VM. Accept the suggested default settings for your first VM; set the o/s type to Linux, though, and the CD/DVD device to your system's actual CD/DVD drive.

Then start the new VM. It may come up telling you there's no system on the drive; in that case put your live CD disk in the reader, and start the VM again. It should then boot from the live CD, just as your real system did originally. Tell it to install. It won't overwrite your real installation; the new VM's "hard drive" is actually a file located on your real disk, but the VM can't tell the difference. Once the install process is complete, you can play all you want to in the VM copy with no chance of damage to your real system.

Before doing anything else, though, I would power down the VM, locate its virtual drive's file (which will have a name ending in ".vdi" and will be in a subdirectory of your home directory) and copy that file to a different name such as "MyVM_backup.vdi" for safety's sake. If your experimenting then clobbers the VM, you can just copy that backup file over the original, and restore everything at once.

I may have to do just that with one of my production VMs, which seems to have suffered some damage to its WinXP Pro system. Unfortunately my backup copy is more than a year old, so I'll have to copy my essential data off somewhere else before doing the restore!

Incidentally, if you're using the new Unity interface, the menu bar for your running VM will be hidden beneath its title bar, making some tips you'll get (such as how to install the Extension Pack) unusable. You can select the Gnome interface on the login screen that asks for your password, to get around this problem. There may be other ways to solve it as well, but this seems to be the simplest.

---

### Post by Ms. Daisy on 2011-11-01
Thanks for the instructions, I'll give VM a go.

---

### Post by Slim Odds on 2011-11-01
> **JKyleOKC said:**
> <cut>

Then start the new VM. It may come up telling you there's no system on the drive; in that case put your live CD disk in the reader, and start the VM again. It should then boot from the live CD, just as your real system did originally. Tell it to install. It won't overwrite your real installation; the new VM's "hard drive" is actually a file located on your real disk, but the VM can't tell the difference. Once the install process is complete, you can play all you want to in the VM copy with no chance of damage to your real system.

<cut>

It's far faster and easier to just use the ISO file to install.

---

### Post by JKyleOKC on 2011-11-01
> **Slim Odds said:**
> It's far faster and easier to just use the ISO file to install.Agreed, but only if you have the ISO file on your host system already. Since the OP is a recent convert to Ubuntu, I figured that she probably burned the ISO from Windows and then installed from the Live CD. However if I was wrong, and the ISO file is on her host system (probably in ~/Downloads, on Xubuntu at least) then it would be much simpler to set the VM's CD to the ISO file. In fact, I've copied all of my master install CDs to my host as ISO files, and use those when creating a new VM.

---

### Post by Paddy Landau on 2011-11-02
A virtual machine is a "pretend" computer. Anything on that machine thinks it is a real computer, but it is "shielded" from the real computer. Even a virus on a VM cannot do anything outside it. Be aware that when running a VM, your computer will be slower (because it will be running two systems at the same time). If you have little RAM, it can seriously affect your response.

> **JKyleOKC said:**
> That's correct, but it's not hard to do. First, install the VirtualBox program using Synaptic (or download it from the Oracle site at [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads) which has a link to the most current release, customized for Ubuntu users; be sure to also download the Extension Pack so that you can use USB devices).
A number of people have found problems with the version in the repository. Rather use the download link that JKyleOKC gave.

> **JKyleOKC said:**
> Before doing anything else, though, I would power down the VM, locate its virtual drive's file (which will have a name ending in ".vdi" and will be in a subdirectory of your home directory) and copy that file to a different name such as "MyVM_backup.vdi" for safety's sake. If your experimenting then clobbers the VM, you can just copy that backup file over the original, and restore everything at once.
It's so much easier to create snapshots. They are almost immediate to create and restore.

> **JKyleOKC said:**
>  Incidentally, if you're using the new Unity interface, the menu bar for your running VM will be hidden beneath its title bar...
Thanks for the heads-up. I haven't used VirtualBox in Natty yet. I'll do so and post here if I find a solution to this problem.

---

### Post by Grenage on 2011-11-02
If it all goes wrong, you can simply roll-back/replace your VM; you probably won't waste waste much time figuring out what went wrong and how to fix it.

You can learn a lot when things go wrong, so it's worth trying to fix problems, even in a VM.

---

### Post by JKyleOKC on 2011-11-02
> **Paddy Landau said:**
> It's so much easier to create snapshots. They are almost immediate to create and restore.That they are, but if the base copy of the VM gets corrupted they're useless. It doesn't happen often, but it's possible and the copy is inexpensive. That's why I recommend making a full copy of the virtual disk file.

I've had a VDI file get truncated during a write operation, for some reason I've never been able to determine, and the "current state" snapshot was no help at all. If I had made a backup copy of the file I could have been back in action in a few minutes -- but I hadn't, so I had to re-install the o/s and then all of the additional programs, losing some six months worth of saved email messages and customer contact information. I now backup the email files nightly, but rely on a backup copy of the VDI file made after the recovery so that I won't have to go through the reinstallation again.

---

### Post by Paddy Landau on 2011-11-02
> **JKyleOKC said:**
> If I had made a backup copy of the file I could have been back in action in a few minutes...
Well, yes; but backups are always strongly recommended. You should have made backups of your emails and customer information anyway.

And I back up my VM disks when they are important to me.

---

### Post by WasMeHere on 2011-11-03
> **Ms. Daisy said:**
> So would it be prudent to run terminal in a virtual box or sandbox when playing around with bash? Can that even be done? Or maybe there's some sort of test mode, where bash will tell you what will happen if you execute a command but without actually executing the command?  I've seen that feature on some software, don't know if it extends to terminal by itself.  Certainly I'm not the first person that needs to be saved from themselves in bash.
I'll answer/comment on this one, although I have also read the following discussion about virtual machines. I think it is very valuable to use virtual machines for testing, and I often run them directly off iso-files (as suggested here).

But sometimes I think it is good enough to test a find, for or while command line with ***echo***, e.g. ```
find * -name '*.odt' -exec echo do-this-with {} \; #################
``` and if it looks good remove the echo and run the real command.

---


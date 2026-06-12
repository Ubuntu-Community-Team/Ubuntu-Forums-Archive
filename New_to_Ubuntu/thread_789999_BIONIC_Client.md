---
title: "BIONIC Client"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by nina_aoki on 2008-05-11
Hi guys --

Does anyone have any experience using and installing the BIONIC client?  I'm able to find and install the BIONIC manager but cannot seem to find the client software to attach to my project.

There seems to be a client download from this site here:

[http://boinc.berkeley.edu/download.php](http://boinc.berkeley.edu/download.php)

Which says:

>  The current release is known to work with these Linux versions:

    * Fedora Core 7 and 8
    * Debian 4.1
    * Ubuntu 7.10 

This is the filename of what I'm able to download.

> 
boinc_ubuntu_5.10.45_i686-pc-linux-gnu.sh

I can download the file but I don't know what to do with it or how to install it now that I have it?  

I know - dummy, right?

Any help would be most appreciated!  ;)

Thanks much,

- nina

---

### Post by Monicker on 2008-05-11
You need to run the following:

```
sh boinc_ubuntu_5.10.45_i686-pc-linux-gnu.sh
```

More details can be found here:  [http://boinc.berkeley.edu/trac/wiki/ReleaseNotes]("http://boinc.berkeley.edu/trac/wiki/ReleaseNotes")

---

### Post by nina_aoki on 2008-05-11
@Monicker

Wow!  Thanks so much!  Great!  I can figure this out from here (I think!)  ;)

Thanks much!

- nina

---

### Post by MaindotC on 2008-05-11
My understanding was that didn't show the nice bar graph that it shows in windoze.  Do you confirm that?

---

### Post by nina_aoki on 2008-05-11
Hmmm... I'm getting a **can't open file.** in my terminal.

Would I have to move the downloaded package to a certain directory you think?

- nina

---

### Post by MaindotC on 2008-05-11
Check permissions to see if it's executable.  Also, try opening it as sudo.

---

### Post by nina_aoki on 2008-05-11
@strAlan

> Also, try opening it as sudo.

Okay -- just so I understand.  I would replace the **sh** in the above listed command line with sudo?  I'll try that and check permissions.

Thanks!  ;)

- nina

---

### Post by MaindotC on 2008-05-11
No, you type:
```

sudo sh boinc_ubuntu_5.10.45_i686-pc-linux-gnu.sh

```

---

### Post by nina_aoki on 2008-05-11
@strAlan

Hmmm. No that didn't work either.  :(

I checked permissions and have everything set to read/write and allowed to execute as a program.  Still getting 'can't open' returns from my terminal.

This is odd!  

But thanks for the suggestions!  ;)

- nina

---

### Post by autocrosser on 2008-05-11
What I do is run a terminal &:
1. chmod 777 sh boinc_ubuntu_5.10.45_i686-pc-linux-gnu.sh
[FONT=monospace]2. run [/FONT]sh boinc_ubuntu_5.10.45_i686-pc-linux-gnu.sh
It will then tell you to start the boinc manager

It has created a folder called "BOINC" in your user /home
you will need to modify the run_manager script (or check to make sure it's right)
It looks like: cd "/home/"your-user"/BOINC" && exec ./boincmgr $@ (make sure that "your-user" is the correct /home for you.

Next you need to attach to a project--most people run SETI@Home.

Any questions--ask me (you can PM me if you wish)

You should not sudo the script--it will lock the BOINC folder.

I'm currently testing with the BOINC Alpha project & can most likely steer you the right way.

---

### Post by nina_aoki on 2008-05-11
Duh!

I'm such a dope!  lmao!

I just doubleclicked it and it asked me if I wanted to run in a terminal.

It just installed...

(yes I ate a brain tumor for breakfast)

Thanks guys! ;)

- nina

---

### Post by nina_aoki on 2008-05-11
@autocrosser

Thanks!  Yeah -- that's the project I'm trying to connect to.  I now have the Bionic folder on my desktop -- but it appears to be installed.  And I've also installed the Bionic Manager -- so we'll see how much more I can screw this up tonight!  ;)

Thanks!

- nina

ps -- Thanks also for the offer for help and walking me thru!  I have the feeling I might need to ask!

---

### Post by MaindotC on 2008-05-11
This is what I got when I downloaded and ran:
```

311-laptop:~/Desktop$ sh boinc_ubuntu_5.10.45_i686-pc-linux-gnu.sh 
use /home/a34lkj2348dsf311/Desktop/BOINC/run_manager to start BOINC
311@a34lkj2348dsf311-laptop:~/Desktop$ ls
BOINC  boinc_ubuntu_5.10.45_i686-pc-linux-gnu.sh
311-laptop:~/Desktop$ cd BOINC/
311-laptop:~/Desktop/BOINC$ ls
binstall.sh  boinc_cmd  boincmgr.16x16.png  boincmgr.48x48.png  locale      run_manager
boinc        boincmgr   boincmgr.32x32.png  ca-bundle.crt       run_client

```

If you can't get it to run, want me to just zip the contents and you can download them?

---

### Post by MaindotC on 2008-05-11
Bah...foiled by the quick hands of that double autocrosser!

---

### Post by autocrosser on 2008-05-11
Wow---never heard my nic used like that--Very Good!!!

---

### Post by nina_aoki on 2008-05-11
@strAlan

> Bah...foiled by the quick hands of that double autocrosser!

lol!  Oh don't worry, knowing me I'll find some way to make this not work and will be crying for help again soon! haha!

Thanks again! ;)

- nina

---

### Post by autocrosser on 2008-05-11
Luck to you--I'm going to check my eBay stuff & crash---Problems--just ask...

---

### Post by stella2657 on 2008-05-11
hi - i have found the quickest way to get bionc up and running is to enable third party software and install both the bionc client and manager via synaptic this will give you a slightly older version with a a little slower wu turnover, but it takes the hassle out of doing it, from the command line.

---

### Post by autocrosser on 2008-05-11
Yes--that installs the 5.8.16 client--Also it installs things where I don't want them. I like having everything installed in my /home so if I reinstall it's not touched & is easy to move between both my installs.

I do testing & so I keep 2 /home(s) on seperate partitions & sync/update them weekly so if I have a "blowup" in the testing branch, I can just reboot into the current stable one--sync the difference from my last update & just keep on working.

You only need to use the terminal when you install a new version--I create a menu item & use the run_manager script to call it.

There is a good source for optimized clients at: 
[http://lunatics.kwsn.net/](http://lunatics.kwsn.net/)

Their clients cover all the current AMD & Intel hardware, are correct for SETI crunching (coded by CrunchR who works with SETI) & are visibly faster that the stock unit. More of a pain to install, but I get about 15/20% more WU's done with their Intel SSE3 client.

---

### Post by oldos2er on 2008-05-11
> **nina_aoki said:**
> @strAlan

Hmmm. No that didn't work either.  :(

I checked permissions and have everything set to read/write and allowed to execute as a program.  Still getting 'can't open' returns from my terminal.

This is odd!  

But thanks for the suggestions!  ;)

- nina

 Just FYI, the proper command is "sh ./boinc_ubuntu_5.10.45_i686-pc-linux-gnu.sh"[FONT=monospace]

[/FONT]

---

### Post by nina_aoki on 2008-05-11
@stella2657

> hi - i have found the quickest way to get bionc up and running is to enable third party software and install both the bionc client and manager via synaptic this will give you a slightly older version with a a little slower wu turnover, but it takes the hassle out of doing it, from the command line

Hi there --

Do you know what that client would be called?  I tried looking for one before I went thru all this but could not find it -- which actually surprised me.  I mean, considering how mature an OS Ubuntu has become and how popular Linux/Unix is in the Berkley community -- one would 'think' that something a whole lot simpler would have been released at this point.  

What I'm playing with now feels more like a science project instead of a number cruncher *for* science projects!  ;)

- nina

---

### Post by nina_aoki on 2008-05-11
@oldos2er

> Just FYI, the proper command is "sh ./boinc_ubuntu_5.10.45_i686-pc-linux-gnu.sh"

Thanks Ann!

- nina

---

### Post by nina_aoki on 2008-05-11
@autocrosser

> Their clients cover all the current AMD & Intel hardware, are correct for SETI crunching (coded by CrunchR who works with SETI) & are visibly faster that the stock unit. More of a pain to install, but I get about 15/20% more WU's done with their Intel SSE3 client.

I think I'm going to take you up on your offer!  ;)

I'll likley PM you with where I am now if that's okay -- but probably not today.  It's Mother's Day and I'm playing queen and I don't think my brain is up for the heavy lifting!  lol!

I'd really like to get it working properly too -- I've got three machines now running Ubuntu in my office and I'd like to use those spare computer cycles to listen to Vega! haha!

Thanks much!

- nina

---

### Post by Tomatz on 2008-05-11
> **Monicker said:**
> You need to run the following:

```
sh boinc_ubuntu_5.10.45_i686-pc-linux-gnu.sh
```

More details can be found here:  [http://boinc.berkeley.edu/trac/wiki/ReleaseNotes]("http://boinc.berkeley.edu/trac/wiki/ReleaseNotes")

You need to change to the directory the executable is in.

E.g

If the **boinc*.sh** is on the desktop:

```
cd ~/Desktop
```

then

```
sh boinc_ubuntu_5.10.45_i686-pc-linux-gnu.sh
```

;)

---

### Post by autocrosser on 2008-05-11
Not a problem--I'd remove the BOINC folder from your desktop & just put it into your /home--You will need to change the run_manager script to reflect the location change--I can guide you on that.

As for Lunics--you'll need exactly what machine(s) specs are to use the proper optimized client. I can write a tutorial for you to set up everything. I'm running two units-One is a Core Duo (2.66 running at 3.2) & a Pentium Dual 940 (running at 3.4) & I'm a member of SETIUSA....

Heading to lunch with mom---talk about it later.....



> **nina_aoki said:**
> @autocrosser

I think I'm going to take you up on your offer!  ;)

I'll likley PM you with where I am now if that's okay -- but probably not today.  It's Mother's Day and I'm playing queen and I don't think my brain is up for the heavy lifting!  lol!

I'd really like to get it working properly too -- I've got three machines now running Ubuntu in my office and I'd like to use those spare computer cycles to listen to Vega! haha!

Thanks much!

- nina

---

### Post by wawadave on 2009-03-13
any one try doing?
sudo apt-get install boinc-client

---


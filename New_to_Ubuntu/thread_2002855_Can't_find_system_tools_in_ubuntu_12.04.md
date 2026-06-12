---
title: "Can't find system tools in ubuntu 12.04"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by Nico156 on 2012-06-13
Sorry I try everything I can to find this but nothing found yet..
I need to use grub customizer
I already install it via terminal
I try to launch the app via terminal, it ask me password the process seem done but no app appear on desktop
So I would like to launch app via an icon
thanks

---

### Post by stinkeye on 2012-06-13
Loads ok here in the terminal with... 
```
grub-customizer
```

or just searching in the dash.

version: grub-customizer_2.5.7-0ubuntu1~ppa1p
How did you install?

---

### Post by Nico156 on 2012-06-13
I used this guide:
[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

I did copy and paste terminal commands to do the installation
It seems to install fine because it asked me password and it asked me if I really want to install it also.
Then I used terminal and *gksu grub-customizer  *to launch it and it asked me password, stand by a little time and then nothing appear.

by searching in the dash I can't find it

---

### Post by stinkeye on 2012-06-13
There was build recently in that ppa.
Check update manager to see if there is an update to grub-customizer.
Software Centre is showing this version for me... **grub-customizer 2.5.7-0ubuntu1~ppa1p**

---

### Post by Nico156 on 2012-06-13
I can't find even in the software center! I don't know what to say..
Tried to search, tried under history, installed.. nothing found..
Ok I'm going to find the grub file and try to edit with a text editor

---

### Post by stinkeye on 2012-06-13
Check your software sources for the ppa.

---

### Post by Nico156 on 2012-06-13
Ok I did not installed it, now I type by hand in the terminal and the install process go well.
I can find it in the dash!
But.. When I click on the icon nothing appears..

---

### Post by stinkeye on 2012-06-13
Just a note ,when installing using
```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
```

You need to copy and paste each line one at a time.
After the first command you will be prompted to press **Enter**, to install
the ppa signing key.
Then run the other two commands.

---

### Post by Nico156 on 2012-06-13
You find my past mistake, I know I'm so stupid :-))
But even with a correct install and grub customizer showed in the dash the app wont start..
Now I make a 254 item update and need to restart the laptop I hope it will make the customizer start..

---

### Post by stinkeye on 2012-06-13
> 254 item update
:shock::p

---

### Post by Nico156 on 2012-06-13
where I can find my software sources?

by the way after the restart nothing change..
go to dash click to grub cust icon and dash close and nothing on desktop

---

### Post by Curtis6767 on 2012-06-13
What happens if you do this:

file system/usr/share/applications

Is it in the Applications folder and can you launch it from there?

---

### Post by Nico156 on 2012-06-13
find it, either double click or right button and open did not make any conseguence..
:confused:
I'm logged as administrator, what it could be wrong..

---

### Post by Curtis6767 on 2012-06-13
Open up the Software Center.

Move your mouse up to the top left hand corner of the screen and the hidden menu will appear.

Select  "Edit" and then Software Sources.

Go to the Other Software tab, the same one that stinkeye showed in the other post.

Use Screenshot and capture an image of your software sources and post it back here.

---

### Post by Nico156 on 2012-06-13
ok done

---

### Post by Curtis6767 on 2012-06-13
You've got duplicates of those PPA's so go ahead and de-select one.

Then run these commands in your terminal. Copy and paste them.

       ```
sudo apt-get -f install
``` 

 ```
sudo apt-get update   
```

```
sudo apt-get dist-upgrade  
```

Hope this helps.

---

### Post by Nico156 on 2012-06-13
still doesn't work..

---

### Post by Curtis6767 on 2012-06-13
> **Nico156 said:**
> still doesn't work..

Well, that's the best I can come up with. Maybe someone else will come along with the right answer.

One last thing, turn off your computer, wait for at least a minute, and then turn it back on.

GL

---

### Post by Nico156 on 2012-06-13
ok thanks anyway..

---

### Post by raja.genupula on 2012-06-13
> **Curtis6767 said:**
> You've got duplicates of those PPA's so go ahead and de-select one.

Then run these commands in your terminal. Copy and paste them.

       ```
sudo apt-get -f install
``` ```
sudo apt-get update   
``````
sudo apt-get dist-upgrade  
```Hope this helps.
could you provide us the output of those commands , any errors you got there ?

---

### Post by stinkeye on 2012-06-13
> **Curtis6767 said:**
> You've got duplicates of those PPA's so go ahead and de-select one.



That's normal when adding a ppa.
One is for source code.

---

### Post by Curtis6767 on 2012-06-14
Made a couple of errors in my attempt to help OP.

Bump this up so maybe OP will see it's not over yet.

My apologies

---

### Post by Nico156 on 2012-06-14
> **raja.genupula said:**
> could you provide us the output of those commands , any errors you got there ?

so I can re-type those commands without uninstall customizer?

---

### Post by Nico156 on 2012-06-14
> **stinkeye said:**
> That's normal when adding a ppa.
One is for source code.

so I have to select it again, so both of those must be ''on''?

---

### Post by Nico156 on 2012-06-14
> **Curtis6767 said:**
> Made a couple of errors in my attempt to help OP.

Bump this up so maybe OP will see it's not over yet.

My apologies

Don't worry you have been gentle to help me! :-)

---


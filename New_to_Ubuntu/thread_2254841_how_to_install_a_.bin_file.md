---
title: "how to install a .bin file?"
date: 2014-11-30
forum: New to Ubuntu
---

### Post by alexei3 on 2014-11-30
I am running Ubuntu 14.04 and i would like to install the latest version of unetbootin-608. It is only 585 version in software center. The problem i have is how do i install a .bin file?

---

### Post by nerdtron on 2014-11-30
Unetbootin? Why not download the latest version from their website? [http://unetbootin.sourceforge.net/unetbootin-linux-latest](http://unetbootin.sourceforge.net/unetbootin-linux-latest)

Then you should mark it as executable just like how it is said on their website.
After download, in the terminal:
```
cd ~Downloads
chmod +x unetbootin-linux-608
./unetbootin-linux-608
```

---

### Post by carl4926 on 2014-11-30
> [COLOR=#000000][FONT=verdana]If using Linux, make the file executable (using either the command [/FONT][/COLOR]chmod +x ./unetbootin-linux[COLOR=#000000][FONT=verdana], or going to Properties->Permissions and checking "Execute"), then start the application, you will be prompted for your password to grant the application administrative rights[/FONT][/COLOR]From unetbootin site

---

### Post by alexei3 on 2014-11-30
Have done exactly as you have said but still zilch?

---

### Post by deadflowr on 2014-11-30
> **alexei3 said:**
> Have done exactly as you have said but still zilch?
Sadly, we are not mind readers.
Tell us exactly what you have done, and what has happened.

---

### Post by alexei3 on 2014-11-30
I downloaded the unetbootin-linux-608.bin file from sourceforge and in a terminal i typed:
cd Downloads
chmod +x unetbootin-linux-608
./unetbootin-linux-608

and then nothing? Perhaps its because i left out the .bin file extension?

---

### Post by nerdtron on 2014-11-30
There is no .bin extension when you download unetbootin for linux.

Any errors when you ran those commands? Did unetbootin launched?

---

### Post by alexei3 on 2014-11-30
I did exactly as you suggested in a terminal i typed

cd Downloads
chmod +x unetbootin-linux-608

and finally i typed ./unetbootin-linux-608 but unetboot didn't budge?

---

### Post by nerdtron on 2014-11-30
That is really weird. So I decided to try it out myself.

```
kenneth@nerdtron:~$ cd Downloads/

kenneth@nerdtron:~/Downloads$ ls -l unet*
-rw-rw-r-- 1 kenneth kenneth 4467972 Aug  8 10:56 unetbootin-linux-latest

kenneth@nerdtron:~/Downloads$ chmod +x unetbootin-linux-latest 
kenneth@nerdtron:~/Downloads$ ls -l unet*
-rwxrwxr-x 1 kenneth kenneth 4467972 Aug  8 10:56 unetbootin-linux-latest

kenneth@nerdtron:~/Downloads$ ./unetbootin-linux-latest 
```

It's not even running
```
kenneth@nerdtron:~/Downloads$ ps -ef | grep unet
kenneth  13510 13429  0 11:23 pts/39   00:00:00 grep --color=auto unet
```

Even launching it from the file manager no response. No errors shown for both methods.. Could be a compatibility issue for unetbootin.

---

### Post by alexei3 on 2014-11-30
Now you've completely lost me with all that code lol

---

### Post by bapoumba on 2014-11-30
Should not it run with sudo ?

Edit, not that : make it executable for user and group. Then it runs and asks for my password.

```
bapoumba@bapoumba-utopic:~/Downloads$ ls -la unet*
-rwxrwxr-- 1 bapoumba bapoumba 4467972 nov.  30 20:31 unetbootin-linux-608
```

---

### Post by alexei3 on 2014-11-30
Thanks for all the help nerdtron but it seems as though i am not going to get Unetbootin up and running unless i use the out dated version from the software centre

---

### Post by alexei3 on 2014-11-30
I did try using sudo but with the same result nothing

---

### Post by nerdtron on 2014-11-30
Update: It is compatibility issue.

It just tried this myself:

The latest one compatible with Ubuntu 14.04 is unetbootin 603
Here's the download link: [https://launchpad.net/~gezakovacs/+archive/ubuntu/ppa/+files/unetbootin_603-1%7Etrusty1_amd64.deb](https://launchpad.net/~gezakovacs/+archive/ubuntu/ppa/+files/unetbootin_603-1%7Etrusty1_amd64.deb)

Now go the Donwloads folder and double click the file. The software center should launch and after several seconds you should see Unetbootin install button. Look on the details and it should say it is version 603.

---

### Post by bapoumba on 2014-11-30
@ nerdtron : yes, that should be it :)

---

### Post by alexei3 on 2014-11-30
It was Unetbootin 603-1~trusty1 and installed a treat. Really big thanks nerdtron

---

### Post by carl4926 on 2014-11-30
From the terminal at the Downloads location

```
[COLOR=#000000]*chmod +x ./unetbootin-linux latest*[/COLOR]
```

---


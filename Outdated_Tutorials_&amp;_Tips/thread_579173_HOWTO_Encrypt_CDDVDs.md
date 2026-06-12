---
title: "HOWTO Encrypt CD/DVDs"
date: 2007-10-18
forum: Outdated Tutorials &amp; Tips
---

### Post by ceno-byte on 2007-10-18
HOWTO Encrypt CD/DVDs in Ubutnu

Hello everyone this is my first HOWTO i am writing based on this link
[http://tinyurl.com/36auez](http://tinyurl.com/36auez). I find it pretty useful if you have sensitive data u want to encrypt and burn to a cd or dvd for backup purposes. I know there is a program called truecrypt but because i only run ubuntu i found that truecrypt is a little hard to use from the CLI. The GUI called forcefield i find kinda clunky so this method works best for me unfortunately this method only works on linux and is not cross platform. I hope some other people will find it useful so lets get started shall we. If u decide to use 128bit please use the 128bit commands otherwise use the 256bit commands 

first we need to get the necessary tools
```
sudo aptitude install aespipe mkisofs loop-aes-utils
```

I also recommend making a directory in media so we have a mount point for the iso.
```
sudo mkdir /media/iso
```

Creating the CD/DVD image
Lets first make a directory in your home folder we will call it encrypt.
```
"mkdir encrypt"
```
Now go ahead and drop the files u want to burn into the directory. We are using AES encryption you can choose from 128 or 256 bit encryption

128bit command
```
mkisofs -r encrypt | aespipe -e aes128 > encrypt.iso
```

or

256bit command
```
"mkisofs -r encrypt | aespipe -e aes256 > encrypt.iso"
```

It will now ask for a password i recommend at least a 20+ character password remember it or else you will lose your data.

Mounting the image
First we need to load some modules.
```
sudo modprobe aes
```
```
sudo modprobe cryptoloop
``` 

128bit command
```
sudo mount -t iso9660 encrypt.iso /media/iso -o loop=/dev/loop0,encryption=aes128
```

or

256bit commad
```
sudo mount -t iso9660 encrypt.iso /media/iso -o loop=/dev/loop0,encryption=aes256
```

You can now burn the image but i found if i use the nautilus cd burner it may give you a error stating its a invalid image. I'm not sure if it was just my box or not but if you get the error i recommend using gnomebaker as i was able to successfully burn the image without a problem i did not test it with k3b.

Mounting the new CD/DVD
Make sure you loaded the required modules.
```
sudo modprobe aes
```
```
sudo modprobe cryptoloop
```


The command to mount the CD/DVD

128bit command
```
sudo mount -t iso9660 /dev/cdrom /media/iso -o loop=/dev/loop0,encryption=aes128
```

or

256bit command
```
sudo mount -t iso9660 /dev/cdrom /media/iso -o loop=/dev/loop0,encryption=aes256
```

Then simply enter your password you entered when you created the iso and you should see your sensitive data.

Tested on ubuntu 7.04 32bit i did not test it on any other version of ubuntu but it should work. I do support this thread so if u need help let me know.

---

### Post by db9s on 2007-11-19
Thanks.

How would I do this on the fly? I have like 20 dvds that I want to encrypt. DVD -> encrypted ISO on hd 

Also how would I make it read the same password? Like I want to make sure I don't type it wrong. Preferably read it off a text file.

Is there any equivalent program to open these ISO's on windows?

---

### Post by db9s on 2007-11-21
Also what is the most cross platform method? I want to be able to open these burned ISO's on Windows. Things get a little trickier because the entire CD is encrypted instead of a single file/folder so it doesn't mount properly in Windows in the first place. Is there any program to decrpyt in Windows?

---

### Post by smartboyathome on 2007-11-21
You could always make a shell script which executes all of the commands for you. That will pretty much automate the process.

---

### Post by myharshdesigner on 2007-11-21
thanks :)

---

### Post by db9s on 2007-11-30
yeah but for the password field, it gets a little weird. How do I feed in an input from a shell script? Like it prompts for a password after I run "mkisofs -r encrypt | aespipe -e aes128 > encrypt.iso" 

so how do I feed it a password from a shell script?

---

### Post by dbenc on 2009-04-07
you can use the -p option in aespipe to specify a file with the password in it, one per line.

from the man page:

> -p fdnumber
    Read the password from file descriptor fdnumber instead of the terminal. If -K option is not being used (no gpg key file), then aespipe attempts to read 65 keys from passwdfd, each key at least 20 characters and separated by newline. If aespipe successfully reads 64 or 65 keys, then aespipe is put to multi-key mode. If aespipe encounters end-of-file before 64 keys are read, then only first key is used in single-key mode

---


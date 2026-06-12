---
title: "Need some help installing a file"
date: 2021-01-13
forum: New to Ubuntu
---

### Post by sdantonio on 2021-01-13
Hi

I'm a completely new user to Ubuntu (running 20.4 LTS) and I'm trying to install Impro-Visor.  I have downloaded both the tar and the shell script file and have them in my downloads folder.

I tried installing it using this terminal command chmod +x Impro-Visor_unix_10_2.sh (I pulled this command line from another improvisor thread here) and the terminal responds no such program.  I'm not sure, but I'm assuming it is something incredibly stupid like I'm not directing the terminal to the right folder or something like that.

I'll keep working on it from my end, but any help here would be great since this is an issue that I will no doubt see pop up again as I get more files from sourceforge

Thank you
Steven

---

### Post by tea for one on 2021-01-13
You have to be in the same folder (probably Downloads) to activate the shell script.
```
cd Downloads
```
```
ls
```
Can you see the items that you downloaded?

---

### Post by SeijiSensei on 2021-01-13
If you are in the same directory as the script, you need to precede the filename with "./" like this:
```
./Impro-Visor_unix_10_2.sh
```

---

### Post by yancek on 2021-01-13
```
 chmod +x Impro-Visor_unix_10_2.sh
```

If the instructions told you to run that command, it will only make it executable as it wasn't when downloaded.  It won't run anything.  And if the files are in your Downloads directory  and you want to change to that directory from your /home/user directory, it is:  Downloads with an uppercase D.   The error no such program/file is because you are   not in the correct directory.   Once you are in the correct directory you should be able to run it with the command below.  Be aware of case sensitivity, if the I and V are upper case, you need the command upper case for those letter. 

```
./Impro-Visor_unix_10_2.sh ( 
```

---

### Post by ActionParsnip on 2021-01-14
What is the output of:
```

sudo updatedb
locate Impro-Visor_unix_10_2.sh

```

Thanks

---

### Post by sdantonio on 2021-01-17
Hi Action  I have 2 folders right now, one I created myself. One is downloads which contains the shell script (which is set as executable) and the tar zip for the software.  The second folder is the tar zip, unzipped and it has a copy of the shell script in it that I place there (also executable)

When I try to run the shell script using sudo apt install Impro... I get, package not found
When I just use the command Impro-Visor_unix_10_2.sh it returns command not found

I get the same if I'm in Downloads ir Downloads/Impro_visor10.2 (the unzipped folder)

I think I got it. I was forgetting the ./  I was thinking that was a command to change directories and that it wasn't necessary because I was already in the directory.  I'll let you know if it works

Thanks

---

### Post by sdantonio on 2021-01-17
I got it, it's all up and running. Thanks.  Now if I can figure out how to close this thread :)

---


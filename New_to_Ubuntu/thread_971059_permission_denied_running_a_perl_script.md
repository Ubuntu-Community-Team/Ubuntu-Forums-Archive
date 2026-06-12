---
title: "permission denied running a perl script"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by meniscus on 2008-11-04
I copied a perl script into  /usr/local bin directory. Now when i try to run it from the directory with command 


```
./script.pl 
```

It gives permission denied.

How can i fix this?

Thanks in advance

---

### Post by dracayr on 2008-11-04
why did you copy it to /usr/local/bin? If you did it because you want it to be in your path, copy it to ~/bin instead (create the directory if it doesn't exist). And never give a program that is in your path such a general name. use some name that hints to the use of the script.

anyway, use "sudo ./script.pl" to gain the permission

dracayr

---

### Post by meniscus on 2008-11-04
Thanks for your advice.

I typed in

```
sudo ./script.pl 
```

and it returned command not found!

---

### Post by Gannon8 on 2008-11-04
> **dracayr said:**
> why did you copy it to /usr/local/bin? If you did it because you want it to be in your path, copy it to ~/bin instead (create the directory if it doesn't exist). And never give a program that is in your path such a general name. use some name that hints to the use of the script.

anyway, use "sudo ./script.pl" to gain the permission

dracayr
Or:
```
sudo chown [your username] ./script.pl
```

Probably safer than running the command as root, but if it makes a system change, you will need to run it as root anyway.

---

### Post by Gannon8 on 2008-11-04
> **meniscus said:**
> Thanks for your advice.

I typed in

```
sudo ./script.pl 
```

and it returned command not found!

After copying the script into /bin, don't use ./ Just script.pl

---

### Post by dracayr on 2008-11-04
> **meniscus said:**
> Thanks for your advice.

I typed in

```
sudo ./script.pl 
```

and it returned command not found!

that's strange. what *exactly* does it say?

dracayr

---

### Post by meniscus on 2008-11-04
Sorry to add. 

There are other perl scripts in that folder. But I cant open any of them with text editor. I can open script.pl with text editor though. Do i have to perlise this new script or something?

---

### Post by bodhi.zazen on 2008-11-04
Is the script executable ?

```
sudo chmod a+x ./perl_script
```

---

### Post by dracayr on 2008-11-04
well you can't open them because you don't have the rights to do so. you can gain these rights with sudo. The sudo system is installed on every ubuntu system. But there are reasons why you don't have permissions. If you change something in /usr/bin, you can screw up your system pretty badly. What exactly are you trying to achieve? as I mentioned before, if you only want a private bin directory to put your own programs into use ~/bin (the ~ sign represents your home directory)

dracayr

---

### Post by meniscus on 2008-11-04
Im using smartctl to keep an eye on my hard disk. I found a script that prints the output of smartctl to a file on my desktop. I thought for some reason to put it in my path it had to go in the usr/local/bin folder. Oops 

Yes it was not made executable! Thanks for all your advice. Im starting to understand that i should keep well away from the file system or ill risk messing things up!

---


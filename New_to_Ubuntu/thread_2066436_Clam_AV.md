---
title: "Clam AV"
date: 2012-10-04
forum: New to Ubuntu
---

### Post by Yezinki on 2012-10-04
Hi there,

Installed Clam AV on your recommendations using synaptics & Ubuntu center.

It's AV engine & GUI don't update despite that they are checked?

Tried un installing but wasn't successful.

Could you care to explain how to clean uninstall it & the correct procedure to install for Ubuntu.

Thanks.

---

### Post by NikTh on 2012-10-04
Hi , 

Try 

```
sudo apt-get install --reinstall clamav clamtk
``` 

Then 
```
sudo freshclam
```
The second command is for updating Virus database , but do not bother in future cuz this service runs automatically every-time you boot you OS.

Thanks

---

### Post by Yezinki on 2012-10-04
Thanks NikTh you are one genius member.

Why is there a X sign next to AV engine 0.97.5 & GUI version 4.38?

---

### Post by NikTh on 2012-10-04
> **Yezinki said:**
> 

Why is there a X sign next to AV engine 0.97.5 & GUI version 4.38?

Do not bother . Bugs of GUI 

[https://bugs.launchpad.net/clamtk/+bug/520263](https://bugs.launchpad.net/clamtk/+bug/520263)
[https://bugs.launchpad.net/clamtk/+bug/1052193](https://bugs.launchpad.net/clamtk/+bug/1052193)

```
sudo freshclam
``` do the "job" , as I said it runs automatically in every boot. 

You can check it , if you reboot your pc and then in terminal give this command 
```
dmesg | grep -i clam
```

EDIT: OR ```
ps -A | grep -i freshclam
``` 
and you will see the service up and running.
Thanks

---

### Post by Yezinki on 2012-10-04
Thanks NikTh.

---

### Post by juancarlospaco on 2012-10-04
Hello, i cant fix the old GUI, but i created my own PyQt4 GUI, and its Libre.


[IMG]https://lh4.googleusercontent.com/-wJ0vN3i14pE/UBWjq8a3s7I/AAAAAAAABnE/Ao_5_EZV8Y8/s549/antivirux.jpg[/IMG]


1) sudo apt-get install python-qt4 clamav
2) Download [http://paste.ubuntu.com/1120243](http://paste.ubuntu.com/1120243) save as " antivirux.py "
3) Give antivirux.py executable privileges, execute it, GUI is self explanatory.

---

### Post by Yezinki on 2012-10-04
Thanks juancarlospaco.

Does it function properly?

---

### Post by NikTh on 2012-10-04
> **juancarlospaco said:**
> hello, i cant fix the old gui, but i created my own pyqt4 gui, and its libre.
1) sudo apt-get install python-qt4 clamav
2) download [http://paste.ubuntu.com/1120243](http://paste.ubuntu.com/1120243) save as " antivirux.py "
3) give antivirux.py executable privileges, execute it, gui is self explanatory.

Excellent !! :) 

Thanks

---

### Post by juancarlospaco on 2012-10-04
You judge, the code is there you can read it, nothing to hide, 
works ok here... if it has bug i never noticed.

---

### Post by Yezinki on 2012-10-04
> **juancarlospaco said:**
> 2) Download [http://paste.ubuntu.com/1120243](http://paste.ubuntu.com/1120243) save as " antivirux.py "
3) Give antivirux.py executable privileges, execute it, GUI is self explanatory.


Thanks but save 2 as text antivirux.py?

---

### Post by juancarlospaco on 2012-10-04
> **Yezinki said:**
> Thanks but save 2 as text antivirux.py?

Click on "Download as text" like any normal .txt but instead of ".txt" extension use ".py"

Dont need install, is portable and portatil, can even run from SD or Flashdrive.

---

### Post by Yezinki on 2012-10-04
I get this [http://paste.ubuntu.com/1120243/plain/](http://paste.ubuntu.com/1120243/plain/) when clicked on download?

---

### Post by Yezinki on 2012-10-04
> **juancarlospaco said:**
> Click on "Download as text" like any normal .txt but instead of ".txt" extension use ".py"

Dont need install, is portable and portatil, can even run from SD or Flashdrive.

I don't have SD or Flash drive at the moment what I do? stuck at step 1..........

---

### Post by juancarlospaco on 2012-10-04
Copy and paste the entire code into a .txt file, save it, then rename the file extension from ".txt " to ".py"

---

### Post by Yezinki on 2012-10-04
Done.

now how do I give 3) give antivirux.py executable privileges, execute it, gui is self explanatory.

Sorry to be asking such questions are simple for you but not me.

Appreciate your assistance.

---

### Post by deadflowr on 2012-10-04
To get clamtk to run fully updated, upgrade the version.

go to clam's sourceforge page here:

[http://clamtk.sf.net]("http://clamtk.sf.net")

and instead of clicking on the fat download for ubuntu button, which will only direct to the version in the repos, click on the debian/ubuntu link below that(this is the link to the newer version). Download and open in the software center to upgrade.
When installed clamtk should be fully updated.

---

### Post by Yezinki on 2012-10-04
Thanks deadflowr for the reply & posted link. 
Since I have started & done 2 steps how do i do the last one.....could you care to explain if it's not a bother?

```
3) Give antivirux.py executable privileges, execute it, GUI is self explanatory.
```

---

### Post by Yezinki on 2012-10-04
Is this the terminal command to completely unistalll Clam AV..........

```
sudo apt-get --purge remove clamav clamav-base clamav-daemon clamav-freshclam libclamav2
```

Probably install Avast less pain free.

Thanks.

---

### Post by deadflowr on 2012-10-04
I think you can just right-click the file, go to properties, click on that, go to permissions, and at the bottom below others check mark Allow executing file as a program.
Or in terminal, chmod +x filename. 
Then open the file.

---

### Post by Yezinki on 2012-10-04
Thanks where would the file be?

I have Clam AV installed from step 1.

```
vaio@VGC-LS1:~$  chmod +x antivirux.py
chmod: cannot access `antivirux.py': No such file or directory
vaio@VGC-LS1:~$ 

```

---

### Post by juancarlospaco on 2012-10-05
> **Yezinki said:**
> 
```
vaio@VGC-LS1:~$  chmod +x antivirux.py
chmod: cannot access `antivirux.py': No such file or directory
vaio@VGC-LS1:~$ 

```

This is correct, but antivirux.py need to be on your home folder, the full path need to be like this:

```
/home/vaio/antivirux.py
```

then repeat:

```
chmod +x antivirux.py
```

then run it:

```
python antivirux.py
```

---

### Post by Yezinki on 2012-10-05
Thanks.

---

### Post by Yezinki on 2012-10-05
Thanks juancarlospaco.

1. Reinstalled Clam using

```
sudo apt-get install --reinstall clamav clamtk

```
& 

```
sudo freshclam
```

2. Ran this in terminal your step 1:

```
sudo apt-get install python-qt4 clamav
```

3. Saved this antivirux.py text doc in /home> Documents using Libre Office Writer file but renamed it removed .oct.

4. According to this ```
/home/vaio/antivirux.py
``` results are:


```
vaio@VGC-LS1:~$ /home/vaio/antivirux.py
bash: /home/vaio/antivirux.py: No such file or directory
vaio@VGC-LS1:~$   chmod +x antivirux.py
chmod: cannot access `antivirux.py': No such file or directory
vaio@VGC-LS1:~$ 

```

What am I doing wrong?

---

### Post by Yezinki on 2012-10-05
Used this to uninstall Clam earlier before reinstalling.

```

sudo apt-get --purge remove clamav clamav-base clamav-daemon clamav-freshclam libclamav2
```

---

### Post by Yezinki on 2012-10-05
@ daslinkard could you assist here...........will appreciate it.

---

### Post by lisati on 2012-10-05
> **Yezinki said:**
> Thanks juancarlospaco.

1. Reinstalled Clam using

```
sudo apt-get install --reinstall clamav clamtk

```
& 

```
sudo freshclam
```

2. Ran this in terminal your step 1:

```
sudo apt-get install python-qt4 clamav
```

3. Saved this antivirux.py text doc in /home> Documents using Libre Office Writer file but renamed it removed .oct.

4. According to this ```
/home/vaio/antivirux.py
``` results are:


```
vaio@VGC-LS1:~$ /home/vaio/antivirux.py
bash: /home/vaio/antivirux.py: No such file or directory
vaio@VGC-LS1:~$   chmod +x antivirux.py
chmod: cannot access `antivirux.py': No such file or directory
vaio@VGC-LS1:~$ 

```

What am I doing wrong?

Is the .py file in the Downloads folder? If so, you will need to run the chmod from within the Downloads folder, or move it to your home folder.

---

### Post by Yezinki on 2012-10-05
It was in the Documents folder now I have cut & placed in Home.

---


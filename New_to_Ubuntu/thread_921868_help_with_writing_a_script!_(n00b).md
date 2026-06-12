---
title: "help with writing a script! (n00b)"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by deathvalleyjoker on 2008-09-16
so i bought a Ezonics web cam off of newegg because it was on sale. unfortunately there are no default drivers for it. after some digging in the forums here, i found the following code makes my web cam work after i plug it in: 

```

cd microdia
make
sudo modprobe videodev
sudo modprobe compat-ioctl32
sudo insmod ./microdia.ko

```

The problem is, if i restart or unplug the web cam, i have to enter these same commands in sequence everytime for it to work. 

I was wondering how i could write this into a script that i could run everytime i wanted to activate my web cam. 

Thanks!

---

### Post by Peter Frank on 2008-09-16
Copy these lines into Gedit, and save the file in a convenient place. Right-click the file -> Properties -> Permissions ->Check "Allow Executing File",and click "Close". This is your script file. When you want to run it, double click, and choose "Run in terminal" instead of "Run" because Sudo will ask for your password.

---

### Post by drubin on 2008-09-16
> **deathvalleyjoker said:**
> so i bought a Ezonics web cam off of newegg because it was on sale. unfortunately there are no default drivers for it. after some digging in the forums here, i found the following code makes my web cam work after i plug it in: 

```

cd microdia
make
sudo modprobe videodev
sudo modprobe compat-ioctl32
sudo insmod ./microdia.ko

```

The problem is, if i restart or unplug the web cam, i have to enter these same commands in sequence everytime for it to work. 

I was wondering how i could write this into a script that i could run everytime i wanted to activate my web cam. 

Thanks!

basically put it all in a script file (this is bash scripting).
I am not 100% sure sure of the full paths of the microdia.

```

#!/bin/bash
cd ~/microdia  #this is a comment, assumed that microdia is in your home dir
make
sudo modprobe videodev
sudo modprobe compat-ioctl32
sudo insmod ./microdia.ko

```

Put that in a file called. startwebcam.sh place it on your desktop. and then right click properties->permissions. and check the execute box.

Then you should be able to double click on the file on your desktop.

---

### Post by deathvalleyjoker on 2008-09-16
Thank you i will try this when i return home. Alot easier than i thought it was gonna be...

---

### Post by deathvalleyjoker on 2008-09-16
> **rubinboy said:**
> basically put it all in a script file (this is bash scripting).
I am not 100% sure sure of the full paths of the microdia.

```

#!/bin/bash
cd ~/microdia  #this is a comment, assumed that microdia is in your home dir
make
sudo modprobe videodev
sudo modprobe compat-ioctl32
sudo insmod ./microdia.ko

```

Put that in a file called. startwebcam.sh place it on your desktop. and then right click properties->permissions. and check the execute box.

Then you should be able to double click on the file on your desktop.


could you explain waht the "#!/bin/bash" does please?

---

### Post by drubin on 2008-09-16
> **Peter Frank said:**
> Copy these lines into Gedit, and save the file in a convenient place. Right-click the file -> Properties -> Permissions ->Check "Allow Executing File",and click "Close". This is your script file. When you want to run it, double click, and choose "Run in terminal" instead of "Run" because Sudo will ask for your password.

Nice, You only forgot that you should have the [Shebang]("http://en.wikipedia.org/wiki/Shebang_(Unix)")  as the first line with script files. 
#!/bin/bash

---

### Post by drubin on 2008-09-16
> **deathvalleyjoker said:**
> could you explain waht the "#!/bin/bash" does please?

See ^^ my last post contains info about a link to the Shebang. It basically tells the OS what needs to run this file.

---


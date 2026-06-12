---
title: "Help With Tar.Gz Files"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by Manatee Magic on 2012-04-16
I want to install Keryx. Which is a tar.gz file. how do I run that?

---

### Post by Cheesemill on 2012-04-16
Download the .deb file instead:

[https://launchpad.net/keryx/stable/1.0-release/+download/keryx_1.0-public21_all.deb](https://launchpad.net/keryx/stable/1.0-release/+download/keryx_1.0-public21_all.deb)

---

### Post by mikaelcrocker on 2012-04-16
Hey, on a tar.gz file I typically run `tar -xzvf (filename)`

-x = extract
-z = decompress
-v = verbose
-f = file archive

Hope this helps

---

### Post by Boyntonstu on 2012-04-16
> **mikaelcrocker said:**
> Hey, on a tar.gz file I typically run `tar -xzvf (filename)`

-x = extract
-z = decompress
-v = verbose
-f = file archive

Hope this helps

Where is the tar.gz file located?

In my case I have the file here >  /home/Gsky/driver.tar.gz

Would this be correct?

tar -xzvf /home/Gsky/driver.tar.gz

---

### Post by d4m1r on 2012-04-16
> **Boyntonstu said:**
> Where is the tar.gz file located?

In my case I have the file here >  /home/Gsky/driver.tar.gz

Would this be correct?

tar -xzvf /home/Gsky/driver.tar.gz


Yes, but just to be sure I'd go to /home/Gsky/ instead (using cd).

Then just tar -xzvf driver.tar.gz

---

### Post by Boyntonstu on 2012-04-16
> **d4m1r said:**
> Yes, but just to be sure I'd go to /home/Gsky/ instead (using cd).

Then just tar -xzvf driver.tar.gz

OK, thanks, I finally got it extracted.

A new folder was created in Home.

I renamed it 8187f

in 8187f there is the driver 8187 including a file called 'install'.

What next?

---

### Post by chamber on 2012-04-17
You haven't said what type of file install is.

Were there no installation instructions on the website or in the extracted folder?

If install is a shell file then you can install it by cd'ing to the directory it is located and then running something like

bash install.sh

you really need to give more info.

---

### Post by Manatee Magic on 2012-04-18
> **Boyntonstu said:**
> Where is the tar.gz file located?

In my case I have the file here >  /home/Gsky/driver.tar.gz

Would this be correct?

tar -xzvf /home/Gsky/driver.tar.gz

I have the unextracted file on my desktop. the name is "Keryx.tar.gz" I tried ```
tar -xzvf /desktop/Keryx.tar.gz
``` but it couldnt find the file. what now?

---

### Post by jerome1232 on 2012-04-18
> **Cheesemill said:**
> Download the .deb file instead:

[https://launchpad.net/keryx/stable/1.0-release/+download/keryx_1.0-public21_all.deb](https://launchpad.net/keryx/stable/1.0-release/+download/keryx_1.0-public21_all.deb)

This is the best advice. Packages are beautiful things. Really, save yourself a huge headache and use the .deb.











If you're really determined to mess with that archive of yours, right click it and click "extract here" Have a gander at what's inside. Check the place you got it from for documentation on what is inside the archive and how to install the software. Your going to need to install build-essential plus what ever else the software depends on. From what I can see once you have it extracted you can double click setup.py and select "run in terminal", post back any errors. Seriously though, just get the .deb.

---


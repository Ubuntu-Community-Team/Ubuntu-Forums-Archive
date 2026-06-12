---
title: "install desktop programs?"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by biomedtech on 2008-09-01
A friend of mine is trying to run mythbuntu, and needs to install some separate applications downloaded to his desktop. How do we use the terminal to install applications that are not coming from a repository? Thanks.

---

### Post by jemate18 on 2008-09-01
> **biomedtech said:**
> A friend of mine is trying to run mythbuntu, and needs to install some separate applications downloaded to his desktop. How do we use the terminal to install applications that are not coming from a repository? Thanks.

What have you downloaded? .deb or a .tgz or what type of file?

---

### Post by kvizz on 2008-09-01
sudo dpkg -i yourapplication.deb

---

### Post by iaculallad on 2008-09-01
> **biomedtech said:**
> A friend of mine is trying to run mythbuntu, and needs to install some separate applications downloaded to his desktop. How do we use the terminal to install applications that are not coming from a repository? Thanks.

What type of source file do you have? Tarball? Bin? Deb? RPM?

---

### Post by asadi on 2008-09-01
I have downloaded ubuntu-8.04.1-desktop-i386. The md5 check sum isn't correct. I have a low speed internet connection and i don't want to downland ubuntu-8.04.1-desktop-i386 completely again. Is there a way to find the incorrect file and download just that file.

---

### Post by iaculallad on 2008-09-01
> **asadi said:**
> I have downloaded ubuntu-8.04.1-desktop-i386. The md5 check sum isn't correct. I have a low speed internet connection and i don't want to downland ubuntu-8.04.1-desktop-i386 completely again. Is there a way to find the incorrect file and download just that file.

Nope, it won't correct the problem you're facing since all the MD5 hash that has been read is from the entire ISO file itself and not the files added on the ISO. Better re-download the entire ISO file.

---

### Post by asadi on 2008-09-01
Thank you iaculallad.
I can extract downloaded iso file with no errors. There is a file named md5sum.txt in the extracted folder and it has the md5 of all files in the iso. I can check the md5 of every single file, but how can i download that file if it is corrupted.

---

### Post by iaculallad on 2008-09-01
> **asadi said:**
> Thank you iaculallad.
I can extract downloaded iso file with no errors. There is a file named md5sum.txt in the extracted folder and it has the md5 of all files in the iso. I can check the md5 of every single file, but how can i download that file if it is corrupted.

Try looking at [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by biomedtech on 2008-09-02
> **iaculallad said:**
> What type of source file do you have? Tarball? Bin? Deb? RPM?

It is a .tar file.

---

### Post by iaculallad on 2008-09-02
> **biomedtech said:**
> It is a .tar file.

Usually it's done with:

-Install the essential files:

```
sudo apt-get install build-essential
```

-Extracting of the tarball:

```
tar -xvf filename.tar
```

-Change directory to where you extracted the tarball:

```
cd location_of_extracted_tarball
```

Then:

```
./configure
make
sudo make install

```

But, try first to read any Readme/Install.txt file included in your tarball.

---

### Post by jemate18 on 2008-09-02
> **asadi said:**
> I have downloaded ubuntu-8.04.1-desktop-i386. The md5 check sum isn't correct. I have a low speed internet connection and i don't want to downland ubuntu-8.04.1-desktop-i386 completely again. Is there a way to find the incorrect file and download just that file.

Yes there is/... select a different mirror......

---

### Post by biomedtech on 2008-09-04
Thank you all for your quick reply.

 Iaculallad, thank you for the exposure to more command syntax. My buddy is telling me that Mythbuntu is a very minimal interface, so when I was trying to explain how to edit his repository, he wasn't finding it. I copied your terminal examples and emailed them to him. So far, I haven't heard back on whether he was successful. 

I don't want to guess on the spelling of the application's name (so that I won't insult the developer) but apparently it's some audio file that mythtv needs.

 I've tried to get my buddy to register here, but he would rather plug away indefinitely, or ask questions I can't answer. Thank you for your time.

---


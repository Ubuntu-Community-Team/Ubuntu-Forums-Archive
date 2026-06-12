---
title: "Encrypted Directory"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by crjackson on 2008-11-20
Is there a GUI frontend for making an encrypted folder in my 8.10 home directory? Also is it possible to encrypt my personal home folder, or would that cause issues?

I need to keep all of my James Bondish top secret files from falling into the hands of the wrong government agents.... :popcorn:

---

### Post by shifty_powers on 2008-11-20
might just be easier to use truecrypt...

[http://www.truecrypt.org/](http://www.truecrypt.org/)

you can find a .deb option on their downloads page...

---

### Post by prshah on 2008-11-20
> **crjackson said:**
> Is there a GUI frontend for making an encrypted folder in my 8.10 home directory? Also is it possible to encrypt my personal home folder, or would that cause issues?

I need to keep all of my James Bondish top secret files from falling into the hands of the wrong government agents.... :popcorn:

Unfortunately, no GUI frontend; yet. But creating your personal private folder is easy: see [http://dustinkirkland.wordpress.com/2008/10/03/whats-in-my-encrypted-private-directory/](http://dustinkirkland.wordpress.com/2008/10/03/whats-in-my-encrypted-private-directory/) for a quick example.

Incidentally, all your private files/directories will have permissions of "700" (Seven-nought-nought). Maybe you should call them "Dnob Semaj" files.

---

### Post by nhasian on 2008-11-20
ubuntu 8.10 comes with the ability for each user to have their own private encrypted directory.  from a terminal type:

```
sudo apt-get install ecryptfs-utils
ecryptfs-setup-private
```

---

### Post by crjackson on 2008-11-21
> **nhasian said:**
> ubuntu 8.10 comes with the ability for each user to have their own private encrypted directory.  from a terminal type:

```
sudo apt-get install ecryptfs-utils
ecryptfs-setup-private
```

Two quick questions:

1) I did as you described and it worked just fine. I clicked on a script inside the folder that told it to let me have access. I now have access to that folder every time I login. I thought it would prompt me for a password each time after I logged out. Am I doing something wrong, or is there a way that I can achieve this?

2) I notice that in my right click context menus, I have the option to encrypt a folder and a gui called seahorse pops up telling me something about encryption keys. What does this thing do? Could that possibly be what I'm looking for? If not, how can I unmount the encrypted directory so that it's locked on next login, and also locked (if I want it to be, while I'm logged in?

---

### Post by adult swim on 2008-11-21
im looking for something like that too.  i did the encryptfs thing a while ago and it encrypted a folder but it mounted it at every login and if i unmounted it, every time i closed my lid it would remount.  is there a way to have it set up as a folder that looks innocent enough and when clicked on prompts for the passphrase to mount it?

---

### Post by crjackson on 2008-11-21
> **adult swim said:**
> im looking for something like that too.  i did the encryptfs thing a while ago and it encrypted a folder but it mounted it at every login and if i unmounted it, every time i closed my lid it would remount.  is there a way to have it set up as a folder that looks innocent enough and when clicked on prompts for the passphrase to mount it?

That's exactly what I'm looking for as well...

---

### Post by nhasian on 2008-11-21
actually i havent used the new private encrypted folder tool in ibex yet.  as i understand it automatically decrypts the folder when you log in.  so if you have multiple users, or boot from a liveCD then you wouldnt have access to the data.

personally i like to use Truecrypt.  you can encrypt a file, partition, or an entire device (even a usb hard disk or thumbdrive)

it doesnt create any icons when or menu items when you install it, but you can easily make some buttons to mount or unmount a partition.

---

### Post by Paqman on 2008-11-21
> **nhasian said:**
> 
it doesnt create any icons when or menu items when you install it, but you can easily make some buttons to mount or unmount a partition.

Actually, you will get a menu item for it now. Just reinstalled it myself recently.

---

### Post by crjackson on 2008-11-21
> **nhasian said:**
> actually i havent used the new private encrypted folder tool in ibex yet.  as i understand it automatically decrypts the folder when you log in.  so if you have multiple users, or boot from a liveCD then you wouldnt have access to the data.

personally i like to use Truecrypt.  you can encrypt a file, partition, or an entire device (even a usb hard disk or thumbdrive)

it doesnt create any icons when or menu items when you install it, but you can easily make some buttons to mount or unmount a partition.

Okay, but can it encrypt a folder so that no one can look inside to see it's contents?

---

### Post by Paqman on 2008-11-21
> **crjackson said:**
> Okay, but can it encrypt a folder so that no one can look inside to see it's contents?

Absolutely. In fact it doesn't have to be a folder. The encrypted container can be made to look like anything (at least superficially)

---

### Post by crjackson on 2008-11-21
> **Paqman said:**
> Absolutely. In fact it doesn't have to be a folder. The encrypted container can be made to look like anything (at least superficially)
Okay then, that looks like what I need. I'll try that next...

---

### Post by crjackson on 2008-11-21
Well, I installed it, but I don't understand how to password protect a folder in my home directory.

Exactly what steps do I need to follow to make this happen?

---

### Post by nhasian on 2008-11-22
run truecrypt and click on Create Volume.

Let's create a file container.  Select Standard Truecrypt Volume.  Create a new name for the file you would like to create.  (you will be able to mount this file and use it like an encrypted folder).  Next select the encryption algorithm, the default AES is fine. set the size you would like the file to be like 1 gig for example. finally enter the password you would like to use.  then finish the setup wizard and now you will be able to mount and unmount your encrypted volume.

when you mount your encrypted volume it will require your truecrypt password.  then it may ask you for your superuser password for the mount privileges. 

I know there was a way to be able to mount/unmount without requiring a superuser password...

I also found this howto might make it easier as it has pictures:

[http://maketecheasier.com/truecrypt-encrypt-your-data-the-easy-way/2008/04/17](http://maketecheasier.com/truecrypt-encrypt-your-data-the-easy-way/2008/04/17)

---

### Post by crjackson on 2008-11-22
> **nhasian said:**
> run truecrypt and click on Create Volume.

Let's create a file container.  Select Standard Truecrypt Volume.  Create a new name for the file you would like to create.  (you will be able to mount this file and use it like an encrypted folder).  Next select the encryption algorithm, the default AES is fine. set the size you would like the file to be like 1 gig for example. finally enter the password you would like to use.  then finish the setup wizard and now you will be able to mount and unmount your encrypted volume.

when you mount your encrypted volume it will require your truecrypt password.  then it may ask you for your superuser password for the mount privileges. 

I know there was a way to be able to mount/unmount without requiring a superuser password...

I also found this howto might make it easier as it has pictures:

[http://maketecheasier.com/truecrypt-encrypt-your-data-the-easy-way/2008/04/17](http://maketecheasier.com/truecrypt-encrypt-your-data-the-easy-way/2008/04/17)

I got it going... Sadly however it tends to cause my computer to lock up. Sometimes a hard reboot is required, sometimes ctrl-alt-bkspc will work. I'm finding it too unreliable to depend on.  Manipulating many files brings it down here.

---

### Post by nhasian on 2008-11-24
locking up?  thats strange.  I have an external usb 1TB drive - the entire device is encrypted with truecrypt and i frequently transfer 5-10 gig files back and forth without any problems.

---

### Post by crjackson on 2009-01-14
This appears to be a great solution - [How to create a private encrypted folder]("http://www.ubuntugeek.com/how-to-create-a-private-encrypted-folder-on-ubuntu-810-intrepid.html#more-726")

I haven't tried it yet but I will this weekend. I just thought some else might find it helpful.

---


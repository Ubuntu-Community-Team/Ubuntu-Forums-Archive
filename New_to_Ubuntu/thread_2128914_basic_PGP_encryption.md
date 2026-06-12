---
title: "basic PGP encryption"
date: 2013-03-24
forum: New to Ubuntu
---

### Post by BGThree on 2013-03-24
***Edit:  See my last post in this thread for the solution I came up with.***

I've been looking for a simple Ubuntu PGP guide but everything I've found is either out of date or beyond my comprehension level.  I'm hoping someone can help me out here, because what I want to do is very very simple:

I have two text files.  One is a PGP public key text file (i.e. a text file that begins "-----BEGIN PGP PUBLIC KEY BLOCK----"), and the other is the message text file that I want to encrypt with the public key.

In Windows I would use GPG4Win and import the public key, and then paste the message text into the Clipboard, and then click encrypt.  I am then prompted to choose the public key I want to use for encryption, I select the key I imported, then boom all done - the encrypted text file is generated.  I can open the encrypted text file in Notepad, and it's a plain text file that starts "-----BEGIN PGP MESSAGE-----" and I can paste it into any other program.

I want to do the exact same thing in Ubuntu.

I tried to install GPA in Ubuntu 12.10, but immediately upon installation I get the error "The GPGME library returned an unexpected error.  The error was: General Assuan error.  This is probably a bug in GPA.  GPA will now try to recover from this error."  I also get this error every time I launch GPA.  After clicking close the error disappears and GPA appears to run.  However, when I try to import the public key text file (trying to use the same method I use in Windows that I explained above) I get the "General Assuan error" and GPA basically stops working.

So I'm at a dead end with GPA, probably because of this error.  Google reveals two year old threads with people reporting this error.  Has it been fixed yet?  

Alternatively, is there another way to accomplish my goal with another program?  It seems like it should be pretty straightforward to encrypt a text file with someone's public key.  Is there a simple command line way to do this?

Thanks for any suggestions!

---

### Post by sandyd on 2013-03-24
You can easily encrypt files with seahorse.

Just import the key into seahorse, and then right click on the key and choose "encrypt"

---

### Post by BGThree on 2013-03-28
Thanks for your reply and sorry I took so long to come back to this.  I'm still not sure how to make this work.  In Seahorse I went to File>Import and selected the public key .asc file.  Seahorse then pops up a window saying "data to be imported" and it correctly lists all the key's metadata (key ID, algorithm, fingerprint, etc.) so Seahorse is definitely able to find and recognize the key.  However, when I then click Import, nothing happens.  It is not shown under the "GnuPG keys" section in Seahorse.

I know the key I'm trying to import is valid, because I can successfully use it to encrypt files using GPG4Win on my Win7 computer.

Any ideas what my problem is?

---

### Post by BGThree on 2013-03-28
OK, solved the first problem.  As usual, I'm an idiot.  In the View menu, the default in seahorse is to only display my personal keys.  I needed to change it to show all keys.  Now I can see the key I want to use in seahorse, but when I right click on it "encrypt" is not an option.  The only options are Delete and Properties, and Properties does not have any encrypt options in it.

How do I use a public PGP key in seahorse to encrypt a text file?

---

### Post by BGThree on 2013-03-28
I think my problem is that GPA (which I believe is the back end for everything I'm trying to do???) is simply broken.  I found [this thread]("http://askubuntu.com/questions/116996/how-do-i-encrypt-decrypt-file-within-gedit") where someone suggests installing Geany and a PGP plugin.  I did that and attempted to encrypt a text file within Geany.  If I encrypt using a key _generated_ by Seahorse, encryption works.  If I encrypt using a public key _imported_ to Seahorse I get "General Error" and it closes.  It is suspiciously similar to the "General Assuan Error" I noted above that occured during encryption attempts.

So I think my next step should be to follow the advice in [this thread]("http://forums.debian.net/viewtopic.php?f=6&t=64515") and install an old version of GPA.  Could someone walk me through (or point to an explanation) locating an old version of GPA and forcing the old version to be installed (and not automatically updated to the new non-functional version)?

Of course, if there's any way to make this work without installing an old GPA, that would be preferable.  Thanks!

---

### Post by BGThree on 2013-03-28
Here is the solution I finally came up with.

1.)  Install Geany with the PGP plugin.

```
sudo apt-get install geany geany-plugin-pg
```

2.)  Enable the PGP plugin within Geany by going Tools>Plugin Manager and then checking the box for PGP.

3.)  Import into Seahorse the public key you want to use to encrypt your text file by doing File>Import.

4.)  Change default Seahorse settings to display all PGP keys, not just yours.  View>Any keys

5.)  Now that you can see the public key you imported within Seahorse, right click on it and select Properties.  Check the box that you trust the key, and **_also sign the key._**  Geany will throw an error at you if you do not sign the key first.

6.)  Using Geany, open the text file you want to encrypt, and then go Tools>GeanyPG>Encrypt.  The plain text message is now PGP encrypted. ):P

---

### Post by norcal618 on 2013-04-07
> **BGThree said:**
> Here is the solution I finally came up with.

1.)  Install Geany with the PGP plugin.

```
sudo apt-get install geany geany-plugin-pg
```

2.)  Enable the PGP plugin within Geany by going Tools>Plugin Manager and then checking the box for PGP.

3.)  Import into Seahorse the public key you want to use to encrypt your text file by doing File>Import.

4.)  Change default Seahorse settings to display all PGP keys, not just yours.  View>Any keys

5.)  Now that you can see the public key you imported within Seahorse, right click on it and select Properties.  Check the box that you trust the key, and **_also sign the key._**  Geany will throw an error at you if you do not sign the key first.

6.)  Using Geany, open the text file you want to encrypt, and then go Tools>GeanyPG>Encrypt.  The plain text message is now PGP encrypted. ):P
Dude! Thank you so much! I have searched the web high and low for a solution and this is exactly what i needed!!

---

### Post by silverguy on 2013-06-14
Here is the work around:

    Download and install a copy of GPA 
    After successful installation, you can run GPA by launching it from the Terminal as follows:

    sudo gpa

This should allow you to operate GPA normally. Just make sure you do not launch it from the Ubuntu launcher.

---


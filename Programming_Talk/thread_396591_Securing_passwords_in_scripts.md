---
title: "Securing passwords in scripts"
date: 2007-03-29
forum: Programming Talk
---

### Post by balloons on 2007-03-29
My broker doesn't support direct connect with quicken (not that I want to use quicken anyway) and only allows web connect. I've got a perl script that logs onto the website and downloads the file, using my username and password. The username and password are stored inside the perl script, which is what scares me, as this is sensitive data in clear text.  How can I secure this? I'd also like to automagically get this web connect file imported into gnucash or something similar. So my question is really twofold, I guess.

1) How can I securely use passwords inside a shell or perl script? compile/obfuscate?
2) Is there a solution to better keep track of my investments/finances?
     eg. right now I use scripts and spreadsheets, since no software will do things the way i want them to - namely, automatic download and import of qif/webconnect files, as well as csv, etc.

---

### Post by Jussi Kukkonen on 2007-03-29
> 1) How can I securely use passwords inside a shell or perl script? compile/obfuscate?
You can't. The best you can do is change file permissions so only the executing user can read the file. For added protection, do not use your own user for it, create a new one just for running the script -- that way someone e.g. walking past your machine can't read the file. 

Another secuity problem with scripts like that is the way you call other programs -- *ps* might just show your password to all users while your script is running...

---

### Post by balloons on 2007-03-29
yes i had remembered the ps problem. I was thinking of passing the username and password to the script from an encrypted file. But again I'd have to give the key for the script to work. So I was thinking instead to pass the passwords (or the key) as arguments. Apart from sitting in memory, the passwords should be secure, correct? Is this the best way to implement?

---

### Post by Mr. C. on 2007-03-29
Something in your description doesn't make sense. You say your perl script downloads from your broker using a username/password, but that you are worried about clear text.

All banks require 128 bit security, so any username/password, and statements you download will be via SSL.  How are you connecting with your perl script to the site, logging on, and downloading the data ?

MrC

---

### Post by balloons on 2007-03-29
yes it's a cpan module www:mechanize. since it connects to the site, the username/password is shown in the clear in the script. the data of course is encrypted - but once downloaded it's not of course, unless i encrypt it

---

### Post by Mr. C. on 2007-03-30
Ah, well in that case, I wouldn't worry about it much.  Keep your system secure and configure the correct permissions on the file.

MrC

---

### Post by Ramses de Norre on 2007-03-30
Can't perl read and write to binary files? If it can, you can store your password and such in such a file. It wont be impossible to read it, but it isn't there in clear text no more.

---

### Post by Mr. C. on 2007-03-30
Bits are bits.  If the data is unencrypted, anyone with sufficient skill can read the file.  The key is to maintaining system security.

Use the "od -bc" command to see how easy it is to read data from what you are calling "binary files".

The file can be encrypted, and the perl script can require a password or pass phrase to decrypt the file, but that is no different that just entering the password when the perl script is run.

MrC

---

### Post by balloons on 2007-04-01
thanks mr. c et la. Unfortunately, that's the same conclusion I reached as well. I guess it's best just to keep it out of the script, or keep the system secure and assume the risk - something much easier done in linux :-) Thanks,

---

### Post by johnraff on 2007-10-10
If it's not too late to jump onto this thread...

If it's impossible to store passwords securely for a home-made script, how do graphic clients like Firefox manage? Are they only *pretending* to encrypt your passwords?

Is there some kind of compromise solution that might not be perfect, but is a bit safer than having the p/w in plain text?

(Right now I'm logging into my website with ftp using a ~/.netrc file to hold the p/w. It's got permissions of 600 but if someone read it and got into my site the consequences could be dire... )

---

### Post by dwhitney67 on 2007-10-10
Below I have included a sample script implementing the usage of 'gpg', which can be used to encrypt the contents of a file.  It's in shell script, however I'm sure you can adapt the concept to your perl script.

I think for your needs the basic idea is:
1) create a plain-text file with your password (and other info)
2) encrypt it using gpg and store the encrypted file; dispose of the plain-text file
3) Within the perl  script, decrypt the encrypted file into a plain-text file
4) read contents of plain-text file during runtime of your script
5) delete plain-text file as soon as possible.

Here's just an example of the workings of gpg:
```
#!/bin/sh
echo -n "Enter your password: "
read pass

FILE=~/mypassword
echo $pass > $FILE
gpg -c $FILE
rm -f $FILE

gpg $FILE.gpg
MYPASSWORD=`cat $FILE`
rm -f $FILE

echo $MYPASSWORD
```

Anyhow, I hope this helps.

---

### Post by johnraff on 2007-10-10
Hi, the OP was indeed using perl but I'm still grappling with bash...

Anyway, you've given me some food for thought. I was thinking vaguely something on those lines, but still haven't really got the whole picture with gpg.
When I tried your script gpg asked me for a passphrase to encrypt and then again to decrypt the file - I don't suppose there's any way of feeding in the passphrase automatically?

Thanks for your help, anyway.

---

### Post by dwhitney67 on 2007-10-10
> **johnraff said:**
> I don't suppose there's any way of feeding in the passphrase automatically?

Someplace, somewhere over the rainbow, there needs to be a "key" (e.g. a passphrase) that needs to be stored in plain-text.  Storing it on your computer would defeat the purpose of what you are trying to accomplish - and that's to protect sensitive data.

The best place to keep the passphrase is in your head, the second best place perhaps on a thumbdrive, then perhaps a piece of paper, but under all circumstances not on your system.  If someone finds the passphrase, then they can use it to open the encrypted file.

The script I provided earlier is merely an example.  Try to translate it into perl.  Here's what it is doing in the "first" part:
1) Reading from the user the real password (i.e. the one that is transferred to the banking institution).
2) Writing that password into a file.
3) Encrypting the file with gpg - which will require you to type a passphrase twice (for confirmation purposes).
4) Delete the file containing the plain-text password.

In the "second" part:
1) Use gpg to read the encrypted file (with .gpg extension) - yes, gpg will prompt for the passphrase that only you would know.
2) Extract the contents of the plain-text file created and stuff into script variable MYPASSWORD.
3) Delete the plain-text file.

What you do with the contents of MYPASSWORD (which is in RAM) is up to you.

---

### Post by johnraff on 2007-10-11
> **dwhitney67 said:**
> Someplace, somewhere over the rainbow, there needs to be a "key" (e.g. a passphrase) that needs to be stored in plain-text.  Storing it on your computer would defeat the purpose of what you are trying to accomplish - and that's to protect sensitive data.Hmm... true of course, but to come back to my previous question, are Filezilla, Firefox, Thunderbird... just *pretending* to store our login passwords securely? *If* they can do it, why can't we?

Anyway gpg and ecrypting/privacy in general looks pretty complicated. I've searched for tutorials and found a couple that fellow-beginners might find interesting:
[http://www.hlug.org/presentations/gpg/gpg.html](http://www.hlug.org/presentations/gpg/gpg.html)
[http://www.glump.net/dokuwiki/gpg/gpg_intro](http://www.glump.net/dokuwiki/gpg/gpg_intro) (for Windows but most of it applies to Unix too)
And this one on using gpg with php scripts:
[http://devzone.zend.com/node/view/id/1265](http://devzone.zend.com/node/view/id/1265)
About 2/3 the way down this last one the "--passphrase-fd" switch is mentioned. (The gpg man page is *huge* and I hadn't found that option.)

Of course you're right that nowhere on the computer is safe for storing the passphrase, but I'm wondering about this compromise:

My present situation:
Home computer with only trusted users, so acess via the net/trojans etc are the only worry.
ftp login username and password are stored in plain text on ~/.netrc which is a well-known file in an obvious location, even though it's permissions are 600.

Possible improvement?:
Store .netrc in encrypted form with another name in another location. 
Store the passphrase in another file with a totally unrelated name in another location.
The script gets the passphrase and uses it to regenerate .netrc temporarily with gpg as you suggested, does the ftp stuff, then deletes it.
All files get permissions of 600 or 700.

Why do I think that might be an improvement?
*An intruder would have to be able to *execute* the script in order to get the ftp password instead of just reading it from the .netrc file.  (Maybe the script could store the file location in some obscure way to add another layer of obfuscation...)
*The script itself would just be one among many- how would they know it can give them the ftp password?

Does that seem to make any sense?

---


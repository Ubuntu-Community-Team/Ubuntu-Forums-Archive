---
title: "how can i right click password protect a file/folder in ubuntu?"
date: 2013-08-21
forum: New to Ubuntu
---

### Post by tojonukokhadush on 2013-08-21
okay i have this text file in gedit in my desktop like for note keeping! i do not expect this file to be accessed by everyone! i need to password protect it. how can i do this in ununtu?

please do not suggest me the crypt-keeper! it's clearly i do not want to keep all the secret files inside the locked box called "crypt-keeper"!! the problem with that is you need to every time unlock that box to access anything inside; that's simply cumbersome! 

what i plainly want is just right click the file and password protect that particular file so that when i next time double click on it to open; it asks for the password!!

and i expect the same to happen for folders even!

HOPE, i put it all simple :-D

---

### Post by Dennis N on 2013-08-21
You can encrypt/decrypt a file from the terminal with gnupg, but it does not meet your "right-click" criterion, so I won't go into details. If you want to know more, ask about it.

---

### Post by tojonukokhadush on 2013-08-21
okay, let me know that as well! like i need to work only once before i open it and then its all secure from others after i close it, right?

---

### Post by Dennis N on 2013-08-21
Open terminal. Change working directory to location of the file. 
Encrypt:
**gpg -c filename**
It will ask for a password. Think one up and remember it. This same password will be used to decrypt (symmetric encryption). 
Result is a file, filename.gpg
To decrypt filename.gpg:
**gpg -o outputfile -d filename.gpg**
Enter the password.
Result is a decrypted file, outputfile 

If you omit the output file option, the decrypted file will write to the terminal instead.
Note: when you encrypt, the original file remains behind. You need to delete it.

There are lots of online tutorials on gpg which is also used for public/private key encryption. Google "gpg tutorial".

Good luck.

---

### Post by tojonukokhadush on 2013-08-21
okay thanks a lot! i searched about "gpg tutorial" as well; they seemed quite complicated for the newbies! 

i did as instructed but got the following error-(image)

---

### Post by Dennis N on 2013-08-22
It probably worked correctly, but in the screenshot, you are trying to view the encrypted file **a.gpg**. The file **a.gpg** it needs to be decrypted before you can view the contents:

```
gpg -o <filename-for-decrypted-file> -d a.gpg
```

(you could look at a.gpg in a text editor, but would only see a string of scrambled unreadable characters.)

**Tip:**
It helps to use an extension on the file you are encrypting so that when you want to decrypt it again, you (and the computer) know how to open the resulting decrypted file. **sample.txt** will encrypt into **sample.txt.gpg**. Later, when you want to decrypt this back to a normal file, it suggests the name you might use for the decrypted file (sample.txt) and the application to open it. 

Note:
You wouldn't use this method to send encrypted files to someone else. That requires public and private keys and is another topic. It also uses gpg, however.

---

### Post by tojonukokhadush on 2013-08-22
okay! thanks a lot!

---

### Post by mastablasta on 2013-08-22
you shouldn't just delete the file you should overwrite it otherwise it can be recovered. propper encypriton programs would do that i believe.

there is a reason why cryptkeeper put them in "a box"

---

### Post by tojonukokhadush on 2013-08-24
like, why isn't there so simple program to password lock individual file/folder in ubuntu? what's the big deal in that?

---

### Post by Dennis N on 2013-08-24
> **tojonukokhadush said:**
> like, why isn't there so simple program to password lock individual file/folder in ubuntu? what's the big deal in that?

A way to password protect with no encrypting is to zip it into a password protected zip file. You can do that with just one file or several files into the same zip archive. You could extract just one from the archive for use.

Try it out.

---

### Post by tojonukokhadush on 2013-08-25
thanks [**[COLOR=#000000]Dennis N[/COLOR]**]("http://ubuntuforums.org/member.php?u=321222")! your help is appreciated! but in a modest sense, what i had expected was to be able to stop anyone from opening my files in the laptop while also being able to give them the privilege of hanging around with my machine ;-)

like, it would be hectic to every time unzip or de-crypt the zipped or encrypted file! but seems that ubuntu does not have such functionality (just prevent anyone opening a file in ubuntu system) :-( which would impress me if there had been a one ;-)

so what i should do now is- the very first time i sit in front of my machine i open the "locked box" (like a one encrypted by creeptkeeper) and not forget to unmount it at last!! :-D HURRAY!

---

### Post by Zill on 2013-08-25
> **tojonukokhadush said:**
> like, why isn't there so simple program to password lock individual file/folder in ubuntu? what's the big deal in that?
No "big deal" at all.  Ubuntu is Free and Open Source Software (FOSS) so you are free to write such an application if you wish.

The rest of us are happy to accept that GNU/Linux is a secure multi-user system and so, if you set permissions correctly, no other users can access *any* of your files.

---

### Post by eternal243 on 2013-08-25
Actually, if I where you I would just create a new user called guest, and they would not be able to reach any files within your home folder, unless you mess up the user permission for guests. That is probably much easier than encrypting and decrypting or password protecting all files that you don't want them to see.

---

### Post by Dennis N on 2013-08-25
Or, you could keep all your sensitive files on a flash drive, and keep it on a chain around your neck, or otherwise secure it on your person (use your imagination)!

---

### Post by tojonukokhadush on 2013-08-25
okay [**[COLOR=#000000]eternal243[/COLOR]**]("http://ubuntuforums.org/member.php?u=483757")[COLOR=#000000]! that was quite responsible answer and sorry [/COLOR][**[COLOR=#000000]Dennis N[/COLOR]**]("http://ubuntuforums.org/member.php?u=321222")[COLOR=#000000][/COLOR][COLOR=#000000] dude, i didn't mean to trouble you![/COLOR]

---

### Post by kmajaa on 2013-11-12
What if I want to send a password-protected file to someone who uses Windows/Mac on a shared computer (it's not theirs) and I don't want anyone else but that person to be able to open this file but I don't want to make it an archive?

---

### Post by shabuboy on 2013-11-12
"i had expected was to be able to stop anyone from opening my files in the laptop while also being able to give them the privilege of hanging around with my machine"


This is what I do...
- Multiple Accts (mine, visitors/guest, browsing)
- I only use mine for sensitive data, access bank accts, etc. password protected and screen lock after x mins.
- If I am just browsing the internet, I use the browsing acct. password protected and screen lock after x mins.
- For friends, visitors, the other acct. No password protected at all.

---


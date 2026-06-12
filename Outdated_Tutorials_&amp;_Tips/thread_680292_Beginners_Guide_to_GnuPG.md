---
title: "Beginners Guide to GnuPG"
date: 2008-01-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Dr Small on 2008-01-27
[center][SIZE="4"]A Beginner's Guide to GnuPG[/SIZE]
[SIZE="7"]&#9617;&#9618;&#9619;»§«&#9619;&#9618;&#9617;[/SIZE][/center]

[SIZE="4"]_Introduction_[/SIZE]

I am going to give a basic run down of how to use GnuPG to encrypt files, sign your messages, read encrypted messages from your friends and whatnot, along with some of useful commands and applications you can use in aiding you along the way :)

First off, incase you don't understand completely (which is absolutely fine, as we are not expected to know everything), GPG is a key-based encryption method. You will be given a public key and a private key. The private key, as indicated, should remain private as to keep the entire idea of encryption secure.

A person who holds your public key and wishes to send you an encrypted message, would encrypt the message with your public key. They can not decrypt their own message after they encrypt it. Only you, who holds the private key can decrypt the message.


[SIZE="4"]_Applications_[/SIZE]

There are two different GUI based applications which can assist you in setting up a GPG key. These two are GPA, which is a very simple application that does everything you need, as far as key managing, deleteing, adding, signing and adding a level of trust to another person's public key.

The second one is seahorse. It is built for Gnome, and uses the gnome-keyring (if I am not mistaken) so it is a little bit more heavy than GPA, which is my favorite. (Note to the reader, I am not a KDE user, but I am sure there is a KDE GnuPG application suited for them. I am in no way discriminating them from this guide for any reason).

Let's begin by installing GPA and seahorse (or you can choose one of the two if you wish).
From the Terminal (Applications > Accessories > Terminal), run the following command:
```
sudo apt-get install gpa seahorse
```

To launch GPA, from run dialog (ALT + F2) or the terminal:
```
gpa
```

To launch seahorse, from the run dialog (ALT + F2) or the terminal:
```
seahorse
```

Both of this GUI applications give you the opportunity to create a GPG key from their menus, and if you wish to do it that way, you may do so. It should be very simple and informational, so I will not explain how to do it from those applications (as it could also be subject to change over time).

Another application worth mentioning would be FireGPG for Firefox. It can encrypt / decrypt / sign / verify / import and export with GPG. To install it for Firefox, please visit their website:
[http://firegpg.tuxfamily.org/?page=install&lang=en](http://firegpg.tuxfamily.org/?page=install&lang=en)


[SIZE="4"]_Key Generating_[/SIZE]

As an alternative, you could create a GPG key from the command line of the terminal.
To do so, launch your terminal (Applications > Accessories > Terminal) and run the following command, to get started:
```
gpg --gen-key
```

You will then be prompted back with the following:
```
Please select what kind of key you want:
   (1) DSA and Elgamal (default)
   (2) DSA (sign only)
   (5) RSA (sign only)
Your selection? 
```

You will want to select number 1, as it can be used for encryption and decryption, whereas the second and third choices are only allowed to sign messages. To do so, press the number 1, and then press enter.

You then will be prompted with the following:
```
DSA keypair will have 1024 bits.
ELG-E keys may be between 1024 and 4096 bits long.
What keysize do you want? (2048) 
```

You will want to enter "2048" here, as recommended by gnupg.
If you don't want your key to expire (for the next prompt, select 0).

Answer yes if the information is correct, when prompted, and then enter your Real Name, Email address, and a comment (which is optional). If everything is correct, press "o" (for Ok) and then enter.

You will then be asked to enter a passphrase. This process will be repeated. As always, make a strong password which would be difficult to crack. Do not enter a name / address / birthdate or word from a dictionary as your password. Take the usual precautions, and make it random and difficult to crack.

After entering your passphrase, follow the instructions in the terminal:
```
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.

```


When you have successfully finished generating your key, you will see a message similar to the following:
> gpg: key **069C39A4** marked as ultimately trusted
public and secret key created and signed.

gpg: checking the trustdb
gpg: 3 marginal(s) needed, 1 complete(s) needed, PGP trust model
gpg: depth: 0  valid:   2  signed:   1  trust: 0-, 0q, 0n, 0m, 0f, 2u
gpg: depth: 1  valid:   1  signed:   0  trust: 0-, 0q, 0n, 0m, 1f, 0u
pub   1024D/**069C39A4** 2008-01-28
      Key fingerprint = 516E E759 94BA 0DC1 37BE  1074 E46C B27D 069C 39A4
uid                  samplekey <samplekey@linux.org>
sub   2048g/BC9EC4CB 2008-01-28


Your KEY-ID would be the two keys (both identical) above which are in bold.
The Key fingerprint is also listed there.


[SIZE="4"]_Key Servers_[/SIZE]

Key servers are used to distribute your public key to other key servers and so other users can easily look your name (or email up) in the database and find your public key to send encrypted messages to you. This eliminates the process of physically or unsecurely giving your friend your public key, and allows others to be able to find you on an online database.

To upload your public key to the Ubuntu keyserver, there are 2 ways to do this.
[LIST=1]
[*]By pasting your ASCII Armored Public Key into the submission box at the Ubuntu Keyserver
[*]By using the terminal and gnupg to send your public key to the Ubuntu Keyserver.
[/LIST]

To accomplish method 1, you will need to open seahorse, select your key under "My Personal Keys" and click the "Export Public Key" in the toolbar. You can optionally choose the name and location of which it will be saved to. Proceed to open up:
[http://keyserver.ubuntu.com:11371](http://keyserver.ubuntu.com:11371)
while opening your newly exported public key with a text editor (gedit).

Select and copy the entire contents of your public key file, and paste it into the "Submit a Key" text area on the Ubuntu Keyserver (link provided above). Submit it, and it should then proceed to submit the key to the keyserver.

You should then be able to search for your email or name in the search string box on the Ubuntu Keyserver page, to find your public key on the internet. This is undoubtedly the Graphical way of doing it, but it can be somewhat longer.

To do it by the means of method 2, you would first need to open up a terminal (Applications > Accessories > Terminal) and paste the following into it:
```
gpg --send-keys --keyserver keyserver.ubuntu.com <KEY-ID>
```

Naturally, you would replace <KEY-ID> with your public key id, as stated before. It also helps to memorize it, like I have done ;)
If you forget what your keyid is, just run:
```
gpg --list-keys <EMAIL>
```

That will list the keys registered with your email (and since there should only be one, it will only list your key.) Then you can obtain your KEY-ID and run the command above, to submit it to the keyservers.


[SIZE="4"]_Importing Keys_[/SIZE]

There are four different methods to importing a key, as stated below:
[LIST=1]
[*]FireGPG
[*]GPA
[*]Seahorse
[*]Terminal
[/LIST]

All are quite simple to do, but FireGPG is the easiest of all if you are importing a public key from a keyserver with Firefox. I will briefly explain all four.

_FireGPG_
If you have somebody's public key on a webpage while in Firefox and have installed FireGPG (as mentioned above under Applications), then simply highlight the Public key from beginning PGP comment to ending PGP comment, right click on it, select FireGPG and click the Import button. It's that simple!

For your information, to solve confusion, the beginning and ending PGP comment tags look like the following:
```
-----BEGIN PGP PUBLIC KEY BLOCK-----
-----END PGP PUBLIC KEY BLOCK-----
```


_GPA_
If someone has given you their public key as a file, simply launch GPA and select "Import" from the toolbar.


_Seahorse_
If someone has given you their public key as a file, you can do one of two things. First, you can open up Nautilus and double click this file, and it should automatically import the public key into your GnuPG, or open Seahorse and select "Key" from the menu and click "Import".


_Terminal_
Open up the terminal (Applications > Accessories > Terminal) and type:
```
gpg --import KEYFILE
```

KEYFILE would be the filename of the public key in your home folder.
(If it is not in your home folder, please cd to the proper directory first, and then run the above command.)


[SIZE="4"]_Tips and Tricks_[/SIZE]

Here is some more valuable information that can be useful when encrypting / decrypting files with GPG from the terminal.

_List Keys_
If you wish to see all of the keys you have imported into GnuPG, you can issue the following command:
```
gpg --list-keys
```


_Encrypt a File_
If you wish to encrypt a file for your friend with his Public Key, run the command in the following format:
```
gpg -o encrypted_file.gpg --encrypt -r <KEY-ID> original.file
```
Explanation:
-o encrypted_file.gpg = Output to the following filename.
--encrypt = Duh, that's the encrypting part :D
-r <KEY-ID> = Recipient. KEY-ID would be your friends KEY-ID here.
original.file = The original file that you will be encrypting.


_Decrypt a File_
If someone has sent you a file that has been encrypted with your public key, you can decrypt it by the following:
```
gpg --decrypt filename.gpg
```


_Clearsign a Document_
Clearsigning is very similar to adding your signature to the bottom of a letter or important paper. It signifies that it actually came from you. By clearsigning, it generates a SHA1 hash of the entire file's contents and add's the SHA1 sum to the bottom of the signature. If the file has been tampered with, the signature verification will fail, which can be used to spot forgery.

If the user has edited the file after it has been signed, the verification of the signature will also fail, because the SHA1 sum will not match that of the actual content.

To clearsign a document / file, run the following:
```
gpg --clearsign filename.txt
```


_Exporting your Public Key_
To export your public key in ASCII Armored fashion, run the following command:
```
gpg --export -a <KEY-ID> > publickey.asc
```

Replace <KEY-ID> with your Public Key ID, and it will create a file called "publickey.asc" which you can distribute to your friends and they can import.


_Symmetric Encryption_
GPG can also do a symmetric encrytion where you can encrypt a file with a passphrase (this is not keybased encryption). To encrypt a file with a passphrase, use this:
```
gpg -c filename.txt
```

To decrypt this type of file, just use:
```
gpg filename.txt
```
And you will be prompted for the passphrase and it will decrypt the file.


**Additional Links:**
[GnuPG.org](http://gnupg.org/)
[GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)
[The GNU Privacy Handbook](http://www.gnupg.org/gph/en/manual.html)
[Wikipedia: GNU Privacy Guard](http://en.wikipedia.org/wiki/Gnupg)

**Related Guides**
[How To: Use GnuPG along with WHIRLPOOL Hash to Encrypt an Individual File](http://ubuntuforums.org/showthread.php?t=939545)
[Advanced GnuPG Concepts - Advanced Key Generation](http://ubuntuforums.org/showthread.php?t=687173)
[How To: Install a Port Knocker - FWKNOP](http://ubuntuforums.org/showthread.php?t=812573)



[B]
[COLOR="DarkRed"]I[/COLOR][COLOR="DarkOrange"]n[/COLOR][COLOR="Olive"]s[/COLOR][COLOR="Green"]p[/COLOR][COLOR="Teal"]i[/COLOR][COLOR="Blue"]r[/COLOR][COLOR="SlateGray"]e[/COLOR][COLOR="DimGray"]d[/COLOR] [COLOR="Teal"]b[/COLOR][COLOR="MediumTurquoise"]y[/COLOR] [URL="http://ubuntuforums.org/member.php?u=257393"][COLOR="Olive"]kevdog
[/COLOR][/URL][/B]

---

### Post by nikoPSK on 2008-01-28
very nice. :)

---

### Post by SOULRiDER on 2008-01-29
Very complete Dr. Small. I may start to build packages soon so I need to knwo how to use GPG :)

---

### Post by Dr Small on 2008-01-29
Thanks for the comments, guys :)

Dr Small

---

### Post by nikoPSK on 2008-01-29
> **Dr Small said:**
> Thanks for the comments, guys :)

Dr Small

oop, forgot to give you your thanks. ;)

---

### Post by Arhuma on 2008-02-01
Hello,

thank you for this wonderful guide! There's still something not quite clear to me::

> 
gpg: key **069C39A4** marked as ultimately trusted
public and secret key created and signed.

gpg: checking the trustdb
gpg: 3 marginal(s) needed, 1 complete(s) needed, PGP trust model
gpg: depth: 0  valid:   2  signed:   1  trust: 0-, 0q, 0n, 0m, 0f, 2u
gpg: depth: 1  valid:   1  signed:   0  trust: 0-, 0q, 0n, 0m, 1f, 0u
pub   1024D/**069C39A4** 2008-01-28
      Key fingerprint = 516E E759 94BA 0DC1 37BE  1074 E46C B27D 069C 39A4
uid                  samplekey <samplekey@linux.org>
sub   2048g/BC9EC4CB 2008-01-28                      
> 
Your KEY-ID would be the two keys (both identical) above which are in bold.
The Key fingerprint is also listed there.
Which is the private key in this example?

---

### Post by kevdog on 2008-02-01
The best way to display the private or public keys on your keyring are:

```

gpg --list-public-keys   <----List public keys
gpg --list-secret-keys  <----Lists private keys
gpg --list-keys <---List all keys

```

---

### Post by Arhuma on 2008-02-01
> **kevdog said:**
> The best way to display the private or public keys on your keyring are:

```

gpg --list-public-keys   <----List public keys
gpg --list-secret-keys  <----Lists private keys
gpg --list-keys <---List all keys

```

If I do:

```

gpg --list-secret-keys

```the result is (as x  example):

```

sec   1024D/069C39A4 2008-01-28
uid                  John Smith  <johnsmith@hismail.com>
ssb   2048g/069C39A4 2008-01-28

```So it's  showing me 069C39A4,  but this is the key ID I use to public my key on keyring servers. It is a public key ID. 

I still don't get it. Which is my private key? How can I see it?

---

### Post by kevdog on 2008-02-01
Im slightly confused.  If you do

gpg --list-secret-keys
gpg --list-public-keys


The results are different.
Look at the results carefully.  The secret keys have sec, ssb and the public keys have pub, sub.

Why do you need to know the difference?  I'm confused.  When you create private encyption and signing keys, the public keys are also put on your key-ring.  They have the same ID.

---

### Post by Arhuma on 2008-02-02
> **kevdog said:**
> 
The results are different.
Look at the results carefully.  The secret keys have sec, ssb and the public keys have pub, sub.


You're right, the results are different, it was my mistake when transcribing. This is what I mean:

If I do <gpg --list-secret-keys> the result is:

** sec**   1024D/**069C39A4** 2008-01-28
uid                  John Smith  <johnsmith@hismail.com>
** ssb**   2048g/**045D39H5** 2008-01-28

If I do <--list-public-keys> it gives me:

** pub**   1024D/**069C39A4** 2008-01-28
uid                  John Smith  <johnsmith@hismail.com>
** sub**   2048g/**045D39H5** 2008-01-28

** pub**   1024D/123F301C4 2008-01-28
uid                  My Friend  <myfriend@hismail.com>
** sub**   2048g/4565A71C8 2008-01-28

So why are my sec and ssb **identical** to my pub 
and sub? Does that mean that also my friend's sec 
and ssb are identical to those I can see? So where
is all the privacy? I'm sorry, I just don't seem to understand.

> 
Why do you need to know the difference?  I'm confused.
I'm just trying to understand how the whole thing works. I've read a lot of documentation out there but it is still not clear to me.

> 
When you create private encryption and signing keys, the public keys are also put on your key-ring.  They have the same ID.
Ok, so what I see out of those commands are not actually the keys but the **keys ID**. Does this mean I'm not allowed to actually see what my private key reads like? I mean, what's the actual sequence  of  numbers and letters for my private key?   

I've been trying to open my secring.gpg  file but have not been able to do so yet, not even as root.

---

### Post by kevdog on 2008-02-02
So you want to see the contents of the public and private keys for example.

The keys are actually in binary format, but you can export the keys in equivalent ascii format to see the difference.

Remember, every key on a keyring there is at least one signing and one encryption key.  The signing key is the primary key, the encryption key is the subkey.

The private keys are kept on the secret keyring and the public keys are kept on the public key ring.  

So lets see if any of the keys differ.  Here is what you gave me:

Public KeyRing
 pub 1024D/069C39A4 2008-01-28
uid John Smith <johnsmith@hismail.com>
sub 2048g/045D39H5 2008-01-28

Private Keyring
 sec 1024D/069C39A4 2008-01-28
uid John Smith <johnsmith@hismail.com>
ssb 2048g/045D39H5 2008-01-28

The public signing key is designated by pub 1024D/069C39A4.  The corresponding private signing key is sec 1024D/06C39A4.  

The public encryption key is designated by sub 2048g/045D39H5.  The corresponding private encryption key is ssb 2048g/045D39H5.

So lets just see if any of these keys differ.  Im going to compare the signing keys (you could do the same for the encryption keys if you want)

gpg --armor --export 069C39A4 > public_signing_key
gpg --armor --export-secret-keys 069C39A4 > private_signing_key

You can compare the two files by doing the following
diff -q public_signing_key private_signing_key
diff -y public_signing_key private_signing_key | more

The first gives you a global summary, the second command will list the files line by line - side by side - so you can compare them yourselves.  You can see the differ.  So that is proof.  You can confirm this with your encryption key sets also, or even compare the public encryption key with the public signing key to prove to yourself the keys differ.  

Convinced yet?

---

### Post by Arhuma on 2008-02-03
> **kevdog said:**
> 
Convinced yet?

Well, all I can say is I've saved this page and keep it in a safe place so that I won't lose it!

Excellent  explanation. Thanks! :)

Arhuma

---

### Post by Dr Small on 2008-02-03
I must say, beautiful explanation!
(Sorry I can't say more, but I'm learning Dvorak and typing is still slow.)

---

### Post by kevdog on 2008-02-03
Off-topic
What's Dvorak?

---

### Post by Dr Small on 2008-02-03
> **kevdog said:**
> Off-topic
What's Dvorak?
[http://en.wikipedia.org/wiki/Dvorak_Simplified_Keyboard](http://en.wikipedia.org/wiki/Dvorak_Simplified_Keyboard)

---

### Post by kevdog on 2008-02-03
Thanks for the link.  I think learning DVORAK would be really hard.  Its would be extremely hard for me to retrain my brain to think like that.  I probably dont type more than 60-70 wpm, however I do so without even thinking about letter placement.  Give me a new letter placement, Im not sure if I could overcome.  Im not very good with learning languages either, so perhaps it uses the same skill set.  Tell me if the experiment works.

---

### Post by gnumd on 2008-03-28
Looks like a nice guide.

Problems I am encountering:
1) There is a difference when running seahorse or GPA from sudo (root) and as listed in this tutorial (not as root).
2) When running per this tutorial seahorse is broken and so is GPA
3) When running from root ie. sudo seahorse it appears to work but doesn't.

What I am able to do is copy over my keys from another machine (using a USB stick) into the sudo seahorse... however running gedit or sudo gedit does not permit encrypting of the text contents.

I get the following error:
> 
Couldn't connect to seahorse-daemon

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I appreciate all help.

-Steve

---

### Post by housam on 2008-05-20
impressive

---

### Post by miloske85 on 2008-07-19
Thanks for the tutorial, it's very nice.

I have one question, what happens with your keys if someone who has physicall access to your pc, resets your password and accesses your user account? I know that XP will destroy your keys in such situation, and attacker won't be able to decrypt your files (EFS), but i'm new to linux, what happens here? And, what would happen with, say, email client (Evolution), would attacker be able to read encrypted emails, and maybe even use the key to encrypt/sign messages that he sends?

---

### Post by Dr Small on 2008-07-19
> **miloske85 said:**
> Thanks for the tutorial, it's very nice.

I have one question, what happens with your keys if someone who has physicall access to your pc, resets your password and accesses your user account? I know that XP will destroy your keys in such situation, and attacker won't be able to decrypt your files (EFS), but i'm new to linux, what happens here? And, what would happen with, say, email client (Evolution), would attacker be able to read encrypted emails, and maybe even use the key to encrypt/sign messages that he sends?
To decrypt, clearsign or change the password on the key, the person who has physical access to the system with your private key would have to enter the password of your private key to unlock it.

Therefore, he would not be able to decrypt, clearsign or reset your password. All should be safe. Of course, unless you have a weak passphrase on your private key.

Dr Small

---

### Post by Paddy Landau on 2008-07-31
I'm afraid I'm totally confused. I come from a PGP-on-Windows background. In Ubuntu, I notice that Seahorse is already installed.

[LIST=1]
[*]I imported my PGP keys into Seahorse successfully.
[*]However, now I have no clue how to use the keys! Someone sends me an encrypted email; how do I decipher it? And how do I encrypt an email back to that person?
[*]In Seahorse, I chose menu options Key -> Back up Key Rings... It saved the key rings as a zip file. How do I restore the key rings (for example if I move to another computer)?
[/LIST]
Thanks

---

### Post by Dr Small on 2008-07-31
Paddy Landau, 

For encrypting / decrypting / signing / verifying, all of this can be done through the command line or with FireGPG for Firefox.
[http://getfiregpg.org/install.html](http://getfiregpg.org/install.html)

As for #3, Seahorse should not have backed up your keyrings as a zip file. I don't recall it doing that. But anyhow, you are supposed to either import them with Seahorse on another computer, or run the gpg --import command in the terminal. Perhaps that there is a file inside of that archive. If so, you would extract it, and then import that file.

Dr Small

---

### Post by Paddy Landau on 2008-07-31
Thanks for the reply, Dr Small.

I've installed FireGPG (lucky I'm a fan of Firefox; what do people do who don't use Firefox?).

[LIST]
[*]I encrypt and sign an email using FireGPG and send it to a Windows machine. The Windows machine (using PGP) happily decrypts and verifies it.
[/LIST]

[LIST]
[*]I encrypt and sign an email on the Windows machine using PGP and send it to the Linux machine. Unfortuately, FireGPG returns an error when attempting to decrypt:
[/LIST]
"Decryption failed. Unknown error. [GNUPG:] NODATA 3"

Do you know how to resolve this problem? (Otherwise, I'll have to send my received PGP emails to a Windows machine to decrypt.)

---

### Post by Dr Small on 2008-07-31
Well, here's the way I would check to really see what the error is in firefox. You can either launch firefox from a terminal, or copy the encrypted message and paste it into a new document called 'crypt' for example.

Then from the command line, run:
```
cat crypt | gpg -d
```

And see what the error output is. Occasionally, I have received the problem that webmail / private messages mess up the formating of it, and render the GPG message void.

---

### Post by Paddy Landau on 2008-07-31
I got the following results.
```
gpg: invalid armour header: www.pgp.com\n
gpg: invalid radix64 character 2E skipped
gpg: invalid radix64 character 2E skipped
gpg: CRC error; 8BFDD0 - 74D283
gpg: packet(3) with unknown version 41
```I don't know what it means, but I'd suspect that the incoming code from PGP is simply incompatible with GPG. Would you agree?

If that's the case, I'll just have to sign into Windows to decrypt these messages.

---

### Post by Drizzel on 2008-09-07
Sorry to bring back an old thread, but I have a question that nobody can answer.. I've been searching google for over a week trying to figure out how to do something that should be very simple. 

How do I use other encryption algorithms in Seahorse? I like twofish and thats what I want to use on my files.. Is there anyway to add twofish to Seahorse? If this cannot be done for some reason, Is there another encryption app that I can use that has more algorithms?

---

### Post by computer_freak_8 on 2008-09-28
> **Drizzel said:**
> Sorry to bring back an old thread, but I have a question that nobody can answer.. I've been searching google for over a week trying to figure out how to do something that should be very simple. 
...
How do I use other encryption algorithms in Seahorse? 
...
Is there another encryption app that I can use that has more algorithms?

I don't believe that Seahorse is compatible with the Twofish algorithm. I'll look into your second question, and then I'll post again.
****Edit: The reason that Seahorse is not compatible with the Twofish algorithm *may* be that GPG/SSH does not support it. I'm not for sure on this one; GPG/SSH may very well support it - I just don't know for sure. It's just a guess.****

---

### Post by computer_freak_8 on 2008-09-28
> **computer_freak_8 said:**
> I'll look into your second question, and then I'll post again.

Ah-ha! I just remembered: Truecrypt. It's open-source, and you can install it by going to [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php) or referring to the How-To at [http://ubuntuforums.org/showthread.php?t=766731](http://ubuntuforums.org/showthread.php?t=766731)


Good luck!
computer_freak_8

---

### Post by kevdog on 2008-09-28
GPG is indeed compatible with the TwoFish symmetric encryption algorithm.  In fact it is ID S10.  Ive never used SeaHorse, however I know for a fact about GPG TwoFish encryption capabilities.  I know how to force the TwoFish encryption algorithm if you want, if not you usually set your personal-cipher-preferences within the gpg.conf file located within ~/.gnupg.  Usually however the cipher selection is set by the recipient's public key, unless you specify something different within the gpg.conf file.

Let me know if you need more info about this!!

Another program if you are interested in encrypting files only is the gpgdir program which can be downloaded here:
[http://cipherdyne.org/gpgdir/](http://cipherdyne.org/gpgdir/)

---

### Post by computer_freak_8 on 2008-09-29
> **kevdog said:**
> GPG is indeed compatible with the TwoFish symmetric encryption algorithm.  In fact it is ID S10.

Thanks! That's why I thought I'd better make note that I was just guessing. 

Good to know. I'll try to remember that.

Thanks again,
computer_freak_8

---

### Post by thecliff on 2010-02-06
Worked extremely well - no issues whatsoever.:D

---

### Post by Oldhacker on 2010-08-02
> **Dr Small said:**
> [http://en.wikipedia.org/wiki/Dvorak_Simplified_Keyboard](http://en.wikipedia.org/wiki/Dvorak_Simplified_Keyboard)
Dvorak was the composer of the "New World Symphony" "Slavonik Dances"
among many others.

---

### Post by kartal on 2010-09-08
Hello

How do I import or use my keys if I move them to another computer or to a newly installed computer?

---

### Post by ka3sem on 2010-10-18
Hi everybody,

I have an encrypted document (with my key) which I should decrypt.
After the generation of my key, my computer is formated and new reinstalled.

Now GnuPG find my key public and I can't use it for decryption!

Do you have a solution for me please? It's very important !!!

---

### Post by ShadowVegan on 2010-10-27
Edit: NVM. Article was helpful, thanks!

---

### Post by 0000_soldier on 2010-12-29
Thank you for tutorial!! and just a quick reply, because some one maybe as stupid as me, this may save them an hour of aggravation! **You cannot encrypt directories**, the saying is true: "never ***-u-me it makes an *** out of me an you" lol. I am a novice, so my ignorance should be forgiven.):P

---

### Post by raokat on 2010-12-29
Thank you Dr. Small. It is really helping me. Most of the issues are very clear now. Thank you once again.

---

### Post by el_diablo on 2011-02-06
[SIZE=4]hello
Can anyone plz explain me in detailed step how to read encrypted mail that i have received by launchpad.I am a beginner in bug tryging.Plz help[/SIZE]......
[SIZE=4]I am not able to validate my open pgp keys.plz help guyz...[/SIZE]

---


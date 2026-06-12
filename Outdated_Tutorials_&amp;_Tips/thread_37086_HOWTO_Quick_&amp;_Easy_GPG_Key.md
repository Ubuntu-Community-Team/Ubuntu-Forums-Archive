---
title: "HOWTO: Quick &amp; Easy GPG Key"
date: 2005-05-25
forum: Outdated Tutorials &amp; Tips
---

### Post by kassetra on 2005-05-25
Note: For this HOWTO you will need to have basic command line/terminal experience, and you will also need the following installed: gnupg, gnupg-agent. In order to create a key, you will also need a real email address.

This HOWTO will take you through a quick & basic PGP Key creation, submission to key servers, and setup in Evolution.  :)

1. Open a terminal.
2. type in the following code:
 ```
gpg --gen-key
``` 
3. Then enter a "1" - to create a standard DSA/ElGamal key.  Press Enter.
4. Type in 1024. Press Enter.
5. Type in 0. Press Enter.
6. Enter a y.  Press Enter.
7. Type in your Real Name.  Press Enter.
8. Type in your REAL email address.  Press Enter.
9. Type in Your First Name, followed by "'s PGP Key".  Press Enter.
10. Type O.  Press Enter. It will now create your Key.
11. You will have to give it a "Pass Phrase" ... usually a short sentence or phrase that isn't birthdays, names, etc. of people in your family. I will say this to you, because when it comes to pass phrases, they're not easy sometimes... so write it down. Because what you DON'T want to do is forget it!!

-
When it's finished creating your Key, follow these steps:
1. Open a terminal.
2. Type in the following code:
 ```
[size=4]**gpg --export -a "User Name" > *public.key***[/size]
``` 
3. Open a nautilus window.
4. Find the file "public.key" in your home directory.
5. Right click on the file, left click on open in text editor.
6. Press CTRL+A, then CTRL+C  (Select All, Copy)
7. Open [http://pgp.mit.edu]("http://pgp.mit.edu") in a browser window.
8. In the box under the label, "Submit a key" - right click in the box and then left click on paste.
9. Click on "Submit this key to the keyserver!"
10. Go back to [http://pgp.mit.edu](http://pgp.mit.edu)
11. Type in your name in the Search String box.
12. Highlight and Copy the section of the result page under "User ID" (It should be your name, comment, and email address.)
 
-
Ok, now that your key has been submitted, add it to your evolution profile:
1. Open Evolution.
2. Go to Edit->Preferences.
3. Choose your email account, click on it, and then click Edit.
4. Click on the security tab.
5. In the PGP/GPG Key ID: box, paste the User ID from the web page result.
6. Click OK.  Click Close.
-
If you want to use your key in any new email, simply click on the "Security" menu item in your new mail message, and then click on "PGP Sign" ... :)


That's it.  You now have your own GPG key.  :)

---

### Post by RastaMahata on 2005-05-25
great guide! I'll follow it right now. I've always wanted a GPG key, as I've heard about security and stuff involving them...
But how does it work? I've heard about pen drive security and other stuff.. :( (I'll google, but if anyone wants to answer... :))

---

### Post by kassetra on 2005-05-26
[QUOTE=RastaMahata]great guide! I'll follow it right now. I've always wanted a GPG key, as I've heard about security and stuff involving them...
But how does it work? I've heard about pen drive security and other stuff.. :( (I'll google, but if anyone wants to answer... :))[/QUOTE]

It works in two separate, but closely related ways:
1. You can now "sign" an email / document, similar to when you sign something in the real world, and because you are the master of the secret key, the recipient of the email / document can be fairly sure that it came from you, and 
2. You can also encrypt an email / document (usually done along with signing it as well) so that your message isn't viewed in transit.  :)

---

### Post by Kyral on 2005-05-26
Why do I sense a new fad coming on?  :-P 

But I'll give it a whirl. Oh, what would the email look like to the person getting it I wonder?

And how would you setup Thunderbird to use this?

---

### Post by Ali_Baba on 2005-05-26
This is interesting HOWTO,I read about Linux Journal that you got a private secret key and a public key.You use secret key to encrypt and then you give your public key to your friend so he/she can decrypt and see your mail using the key. Have to try this myself also :)

---

### Post by Fass on 2005-05-27
[QUOTE=Ali_Baba]This is interesting HOWTO,I read about Linux Journal that you got a private secret key and a public key.You use secret key to encrypt and then you give your public key to your friend so he/she can decrypt and see your mail using the key. Have to try this myself also :)[/QUOTE]

I understood it to work in the completely opposite way. You use other people's public key to encrypt messages to them, and they use their private key to decrypt.

---

### Post by word_virus on 2005-05-27
[QUOTE=Fass]I understood it to work in the completely opposite way. You use other people's public key to encrypt messages to them, and they use their private key to decrypt.[/QUOTE]

Correct.  If you're new to GPG, make sure it's your *public * key you're giving out to others  :) !

---

### Post by kassetra on 2005-05-27
[QUOTE=Kyral]Why do I sense a new fad coming on?  :-P 

But I'll give it a whirl. Oh, what would the email look like to the person getting it I wonder?

And how would you setup Thunderbird to use this?[/QUOTE]

Well, if you just sign it, then it just has this funky little signature thing attached...

Thunderbird.  Hmmmm.  I'm wondering if the procedure is similar, maybe with different menu items and such.

---

### Post by oritpro on 2005-05-27
Excellent guide, thank you!  

Does anybody happen to know of a Linux equivalent to PGP's Encrypted Disk? Preferrably something that can be installed via Synaptic.

---

### Post by Druke on 2005-06-21
[QUOTE=RastaMahata]great guide! I'll follow it right now. I've always wanted a GPG key, as I've heard about security and stuff involving them...
But how does it work? I've heard about pen drive security and other stuff.. :( (I'll google, but if anyone wants to answer... :))[/QUOTE]


It works by use of the RSA (i beleive) one way function basicly your message is transfored to ascii and then a "one way encryption" is performed, this si done by using modular math and a formula that i wont post because i cant find the book where i learned it from  :-P  anyways after alice usees her private key to act upon her message, bob can decrypt it by using the public key to act upon the (secret key ecrypted) ciphertext. 

Anyways my question is how do i encrypt the messages :-p i know how it works i just dont know how to make it work.

thanks in advance

---

### Post by i3dmaster on 2005-06-22
[QUOTE=Druke]It works by use of the RSA (i beleive) one way function basicly your message is transfored to ascii and then a "one way encryption" is performed, this si done by using modular math and a formula that i wont post because i cant find the book where i learned it from  :-P  anyways after alice usees her private key to act upon her message, bob can decrypt it by using the public key to act upon the (secret key ecrypted) ciphertext. 

Anyways my question is how do i encrypt the messages :-p i know how it works i just dont know how to make it work.

thanks in advance[/QUOTE]

well, as long as you know the person's key ID (when the person gives you the public key), then you can use that to sign and encrypt the files. such as
gpg -se -r <bob@foo.com> file(s)...
Then those files are signed and encrypted, when Bob gets the file(s), he can use gpg to decrypt them. For detail usage, you will need to read 1500+ lines of manpage for gpg... :)

---

### Post by sinbad782 on 2005-06-22
You can get the enigmail extension for Thunderbird which interfaces with gpg quite nicely

---

### Post by notos on 2005-06-22
after 
```

gpg --export -a "User Name" > public.key

``` 
i get
gpg: WARNING: nothing exported

---

### Post by nocturn on 2005-06-22
[QUOTE=notos]after 
```

gpg --export -a "User Name" > public.key

``` 
i get
gpg: WARNING: nothing exported[/QUOTE]

Just verifying, but you did change "User name" to your own name?

Alternatively, there is GUI software to do all those things, one is seahorse (in universe I think).

---

### Post by nocturn on 2005-06-22
A very good howto.

I do want to add a recommendation.  When generating the key, choose the biggest length allowed.  Even though 1024 bits is rather secure today, the growing speed of processors will allow it to be cracked much sooner then a 2048 bit key (or larger).

---

### Post by Lunde on 2005-06-22
I did as you explained and it works fine with Evolution, but when I send to my Outlook (Default install), it just shows as a unrecognised attachment.

Then I google **PGP outlook** and I get a lot of **"vulnerability in PGP"**.

Is there a way to proceed so there it will be accepted in other OS's / e-mail clients?

---

### Post by Firetech on 2005-06-22
I had to figure all this out by myself yesterday, just because I didn't find this guide...

Anyway, for those people out there prefering Thunderbird to Evolution, follow Kassetras guide until the evolution part. Then install the "mozilla-thunderbird-enigmail" package with synaptic, kynaptic, apt-get or whatever you like and follow this guide: [http://dudu.dyn.2-h.org/nist/gpg-enigmail-howto.php#t2](http://dudu.dyn.2-h.org/nist/gpg-enigmail-howto.php#t2) (you can skip the step saying "Then, in Enigmail menu, click on 'Generate Key'.")

---

### Post by nocturn on 2005-06-22
[QUOTE=Lunde]I did as you explained and it works fine with Evolution, but when I send to my Outlook (Default install), it just shows as a unrecognised attachment.

Then I google **PGP outlook** and I get a lot of **"vulnerability in PGP"**.

Is there a way to proceed so there it will be accepted in other OS's / e-mail clients?[/QUOTE]

AFAIK, it is hard to get PGP/Mime working in Outlook because Outlook messes with the message content, invalidating the signatures.

I don't know if there is a way arround this yet.

---

### Post by notos on 2005-06-22
[QUOTE=nocturn]Just verifying, but you did change "User name" to your own name?

Alternatively, there is GUI software to do all those things, one is seahorse (in universe I think).[/QUOTE]


yes i did it

---

### Post by angrykeyboarder on 2005-06-24
> Note: For this HOWTO you will need to have basic command line/terminal experience..... As in "sudo apt-get install seahorse" ? ;-)

---

### Post by stanz on 2006-08-06
Is anyone still here...echo....echo ???
I'm in need of trouble shooting help..!?!?
I installed seahorse..with SUID Root, and think that was bad thing.
but, if i change permissions, nothing wants to work cause it insecure
in its own eyes!
and... any commandline in this or other howto/instruct, I must use 'sudo'.
Everyone's making this simple...must I uninstall all, re-install differently?
HELP !!   ](*,)

As usual Thanks in advance!

---

### Post by ktneely on 2007-01-28
> **nocturn said:**
> AFAIK, it is hard to get PGP/Mime working in Outlook because Outlook messes with the message content, invalidating the signatures.

I don't know if there is a way arround this yet.

This is not a direct plugin for Outlook, but if you are using PGP/GPG under windows, I would recommend WinPT  ([http://winpt.sourceforge.net]("http://winpt.sourceforge.net")) as a really good tool to help you with the encryption/decryption and signing of messages and files.

Give it a try.

---

### Post by csaga on 2007-09-01
Hi!
I generated a PGP key but how to import a public key to send encrypted message to another user? I use Evolution mail client.
Thanks for answer!

---

### Post by Gunner_Sr on 2007-12-02
An important part of this process also quoted in the GNU Privacy guard HowTo is the following:

> Keysigning Guidelines

Since a signature means that you checked and verified that a certain public key belongs to a certain person who is in control of the accompanying private key, you need to follow these guidelines when signing peoples keys:

   1. Keysigning is always done after meeting in person
   2. During this meeting you hand each other your OpenPGP key fingerprint and at least one government issued ID with a photograph. These key fingerprints are usually distributed as key fingerprint slips, created by a script such as gpg-key2ps (package: signing-party)
   3. You check whether the name on the key corresponds with the name on the ID and whether the person in front of you is indeed who he says he is.

This important form of security as you need to verify you are actually you to other people otherwise it is pointless.

Cheers,

Gunner_SR

---

### Post by kevdog on 2007-12-03
Not sure if I would recommend this method to anyone currently.  The DSA SHA1 signature hash has been broken -- different sources ending up with the same hash or digest product -- this is known as collisions.

Although this guide is good for the beginner (that is how I generated keys using cygwin for years), recent experience has led me to produce RSA 4096 keys and change the hash and cipher preferences.

Im in the process of writing a guide on how to do these things, however what is difficult is that there is no "gold standard", and you need to understand the implications of the choices you make when generating keys, selecting hashes and ciphers.  Hence Im finding my guide to be rather long since its basically an advanced tutorial how gpg works, how keys are generated, the use of ciphers for encryption and hashes for signatures.

Hopefully others would find this useful as well!

---

### Post by FiReSTaRT on 2009-06-19
Well if you're looking to securely encrypt your data, Truecrypt's probably the way to go. Here's a good primer on it [https://help.ubuntu.com/community/TrueCrypt](https://help.ubuntu.com/community/TrueCrypt) It allows you to create hidden encrypted partitions within encrypted partitions, which can also take the form of a file. You can babushka your sensitive data up the yin-yang if you have the patience (arising from the need) for it.

---


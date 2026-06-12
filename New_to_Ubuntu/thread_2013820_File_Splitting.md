---
title: "File Splitting"
date: 2012-07-01
forum: New to Ubuntu
---

### Post by 3dmatrix on 2012-07-01
Do we have any software to split files for easier transportation or security in Ubuntu software center ?
Like we have Mimar Sinan for windows.

---

### Post by ubudog on 2012-07-01
You may want to check out [Gnome Split]("http://gnome-split.org/"), and the command-line tool 'split', which comes with Ubuntu IIRC.

Is that what you're looking for?

---

### Post by philinux on 2012-07-01
There is also this .

 [http://iloveubuntu.net/split-and-join-files-lightweight-utility-u-splitter](http://iloveubuntu.net/split-and-join-files-lightweight-utility-u-splitter)

---

### Post by HermanAB on 2012-07-01
split obviously and also tar.

---

### Post by cmcanulty on 2012-07-01
I can't find it in SC or synaptic.

---

### Post by ubudog on 2012-07-01
> **cmcanulty said:**
> I can't find it in SC or synaptic.

Neither could I. From what I gather in the man page for it, it comes with the package 'coreutils'.

---

### Post by 3dmatrix on 2012-07-01
I didnt find both of them in Ubuntu software center.

I wish to split any file using 'split' in to several parts and then email them seperately to someone, to be finaly joined together by him. If anyone is able to get hold of any one part will he be able to read its contents ? I mean are the individual parts readable / secure ?

---

### Post by HermanAB on 2012-07-02
Read the tar man page.  It can also compress the file and putting them together again is automatic.

With split, you got to use cat to put them back together in the right order.

---

### Post by 3dmatrix on 2012-07-02
In my previous msg i wrote :

I wish to split any file using 'split' in to several parts and then email them seperately to someone, to be finaly joined together by him. If anyone is able to get hold of any one part will he be able to read its contents ? I mean are the individual parts readable / secure ? 

I wish to know are those individual pieces secure or readable if split by 'split' command ?

---

### Post by sudodus on 2012-07-02
If you want your files to be transmitted securely, you need to encrypt them (before sending) and decrypt them (after receiving). I think this is independant of the splitting. (Encryption can be done 'inside' or 'outside' of the splitting.)

---

### Post by 3dmatrix on 2012-07-02
What if the file is encrypted and split and then joined and then decrypted.
Can that be done ? and in that case is the level of security different ?

---

### Post by sudodus on 2012-07-02
If the splitting program can manage binary files (not text files with regular line feeds), it is possible. It should not change the level of encryption, maybe increase it a little, because the intruder needs to intercept several emails.

---

### Post by Lars Noodén on 2012-07-02
Also, mail is a terribly inefficient way to transfer files.  You might look at one of the file sharing services like Ubuntu One, Spider Oak or one of the many other similar services.

---

### Post by 3dmatrix on 2012-07-02
If its an image file ? Then how should we go abt it ?

---

### Post by sudodus on 2012-07-02
How big is it?

---

### Post by HermanAB on 2012-07-02
All that the split program does, is count off a number of bytes and save it.  It doesn't alter the data in any way.  Using cat, you can glue the parts back together again.  

You should read the man pages. You would have saved yourself a whole lot of time already.

---

### Post by 3dmatrix on 2012-07-02
Well man pages does not tells me anything abt the security aspect which i am more concerned abt or atleast i do not understand it much so i need feedback from ppl having experiencial knowledge with all this.

sudodus : it might not be too big in 'file' size the only purpose of spliting the files is security.

---

### Post by sudodus on 2012-07-02
> **3dmatrix said:**
> Well man pages does not tells me anything abt the security aspect which i am more concerned abt or atleast i do not understand it much so i need feedback from ppl having experiencial knowledge with all this.

sudodus : it might not be too big in 'file' size the only purpose of spliting the files is security.
Use ***gpg*** with private key and public key to send encrypted files. Encryption is ***much*** better than splitting in terms of security.

There is a plugin for gpg encryption of email in Thunderbird: Enigmail.

[[COLOR="Red"]_http://enigmail.mozdev.org/home/index.php.html_[/COLOR]]("http://enigmail.mozdev.org/home/index.php.html")

---

### Post by 3dmatrix on 2012-07-02
> **sudodus said:**
> Use ***gpg*** with private key and public key to send encrypted files. Encryption is ***much*** better than splitting in terms of security.

There is a plugin for gpg encryption of email in Thunderbird: Enigmail.

[[COLOR="Red"]_http://enigmail.mozdev.org/home/index.php.html_[/COLOR]]("http://enigmail.mozdev.org/home/index.php.html")

Well, no matter how well encrypted a file is i some how do not find it safe so i felt useing both methods. Encrypting + spliting. So that even if a person is able to get hold of one part of the file, he will not be able to see the entire picture. Moreover, i may not always email the parts, it might be transported through drives.

So i wish to know :

(1) what is better encryption > splitting or splitting > encryption
(2) in case of picture when a file is split then what is the procedure of spliting ? In other words if there is no encryption then after spliting a picture is it possible to view the pic in each individual parts ?

---

### Post by sudodus on 2012-07-02
> **3dmatrix said:**
> Well, no matter how well encrypted a file is i some how do not find it safe so i felt useing both methods. Encrypting + spliting. So that even if a person is able to get hold of one part of the file, he will not be able to see the entire picture. Moreover, i may not always email the parts, it might be transported through drives.

So i wish to know :

(1) what is better encryption > splitting or splitting > encryption

I think it makes no big difference
> 
(2) in case of picture when a file is split then what is the procedure of spliting ? In other words if there is no encryption then after spliting a picture is it possible to view the pic in each individual parts ?
I don't know, it might depend on the coding of the picture (jpeg, png etc), but I guess it is often sequential, so that part of the picture is stored and might be seen after splitting.

But ...

Have a look at this link: [[COLOR="Red"]_http://xkcd.com/538/_[/COLOR]]("http://xkcd.com/538/")

---

### Post by z3nhakr on 2012-07-02
i saw one called usplit in software center the other day. its compatible with HJsplit for windows. i hope thats helpful (:

[http://apt.ubuntu.com/p/u-splitter](http://apt.ubuntu.com/p/u-splitter)

---

### Post by 3dmatrix on 2012-07-02
> **sudodus said:**
> I think it makes no big difference

I don't know, it might depend on the coding of the picture (jpeg, png etc), but I guess it is often sequential, so that part of the picture is stored and might be seen after splitting.

But ...

Have a look at this link: [[COLOR="Red"]_http://xkcd.com/538/_[/COLOR]]("http://xkcd.com/538/")

Unfortunately that link is not opening.

I have attached two zipped files containing picture and parts after spliting in both png ang jpg format.

As we can see part 1 is fairly easy to make out but i am not sure abt the remaining parts.

.

---

### Post by 3dmatrix on 2012-07-02
> **z3nhakr said:**
> i saw one called usplit in software center the other day. its compatible with HJsplit for windows. i hope thats helpful (:

[http://apt.ubuntu.com/p/u-splitter](http://apt.ubuntu.com/p/u-splitter)

i did not find u split in synaptic.

---

### Post by sudodus on 2012-07-02
> **3dmatrix said:**
> Unfortunately that link is not opening.

I have attached two zipped files containing picture and parts after spliting in both png ang jpg format.

As we can see part 1 is fairly easy to make out but i am not sure abt the remaining parts.

.
Yes, that is reasonable, because the file header is in part 1. So for the rest of the file you need to guess the file header.

---

### Post by 3dmatrix on 2012-07-02
> **sudodus said:**
> Yes, that is reasonable, because the file header is in part 1. So for the rest of the file you need to guess the file header.

Just for my info, if one can guess the file header then how can he see the other parts ? I tried opening the other parts in gimp and image viewer but it does not opens. So what change needs to be made in that file to view them, if i know it is a jpg or png file ?

---

### Post by 3dmatrix on 2012-07-02
Nice attachment ;)
Well i am not trying to be paranoid abt security, its my way of learning and solving problem.

---

### Post by sudodus on 2012-07-02
> **3dmatrix said:**
> Just for my info, if one can guess the file header then how can he see the other parts ? I tried opening the other parts in gimp and image viewer but it does not opens. So what change needs to be made in that file to view them, if i know it is a jpg or png file ?
I don't know the details, but I'm sure there are specialists who know (both good guys and bad guys), because if the information is there and it is not encrypted with a secret key, patterns can be recognized or tested ...

---

### Post by sudodus on 2012-07-02
> **3dmatrix said:**
> Nice attachment ;)
Well i am not trying to be paranoid abt security, its my way of learning and solving problem.
That's a good purpose :KS

---

### Post by z3nhakr on 2012-07-02
> **3dmatrix said:**
> i did not find u split in synaptic.
try searching" u-splitter"

---

### Post by David Andersson on 2012-07-02
> **3dmatrix said:**
> 
 it might not be too big in 'file' size the only purpose of spliting the files is security.

Then I would say you asked the wrong question to begin with. **Splitting** gives virtually no security at all. Unless you split it into millions of individual binary bits and shuffle them. That's what **encryption** does, and then some.

The title should be "secure transfer of a file".

---

If it is about a secure transfer of data between two (or a few) parties, you can use any single key encryption. Only you and your friends know the secret key. You encrypt the file with that key and your friends decrypt the file with the same key.

You can encrypt a file with **gnupg**
```
gpg -c filename.jpg
```
It will ask for a password twice. It will create a new encrypted file filename.jpg.gpg

You or your friend can decrypt with
```
gpg -d filename.jpg.gpg > filename.jpg
```
It will ask for a password that must be the same. The file filename.jpg will be restored (it will be empty if wrong password).

---

Alternatively encrypt with **mcrypt**
```
mcrypt filename.jpg
```
It will ask for a password twice. It will create a new encrypted file filename.jpg.nc

You or your friend can decrypt with
```
mcrypt -d filename.jpg.nc
```
It will ask for a password that must be the same. The file filename.jpg will be restored.

---

Alternatively encrypt with **ccrypt**
```
ccrypt -e filename.jpg
```
It will ask for a password twice. It will *replace* the file with filename.jpg.cpt (that is, filename.jpg is *removed*).

You or your friend can decrypt with
```
ccrypt -d filename.jpg.cpt
```
It will ask for a password that must be the same. It will restore filename.jpg (and filename.jpg.cpt is *removed*)

---

In the above examples, you and your friend use the same key/password. That is called *symmetric* cryptography.

With *asymmetric* cryptography, you have your own secret key (that must be secret, not even your friends may know), plus your own public key (that all your friends must know, in fact, the whole world can know it). Your friends have their own private and public keys, and you know all your friends public keys (and none of their private keys). If you want to send a file that only one person in the world should be able to read, encrypt it with that persons public key, and it can only be decrypted with that persons private key. None of you need to know the other persons private key. (The whole world can know the public keys for both of you, but that is not a problem at all. It is a part of the idea with asymmetric crypto.)

(I won't give any examples for asymmetric encryption here, because there is a bit of setup involved the first time, and I don't know how.)

---

### Post by 3dmatrix on 2012-07-02
Thanx David for the detailed explanation.
I wanted to use both encryption and then splitting the file and transporting them to the destination through multiple routes and then will be joined and decripted back at the destination.
That way even if a person is able to get one or two parts, it will not be of much use as he would not know the password and in case if he is some how able to crack it, it would be not of much help as it would any way be an incomplete image file.
But anyway, thanx for all the info.
I would any way like to write a script to automate the entire work at both ends.

---

### Post by 3dmatrix on 2012-07-02
> **z3nhakr said:**
> try searching" u-splitter"

Sorry, i did not find it.

---

### Post by oldsoundguy on 2012-07-02
This all looks like a whole bunch of work to accomplish what could be done by uploading your file to a personal web space as provided by your ISP and just sending the recipient the link to the file and let them download it.  Then, once the file has been downloaded .. delete it.

---

### Post by David Andersson on 2012-07-02
> **3dmatrix said:**
> 
 and then splitting the file and transporting them to the destination through multiple routes and then will be joined and decripted back at the destination.


The *Internet* does that for you *totally automatically*. Any data, file or e-mail is split into packets, normally of size about between 1 or 2 kilobytes (I think). An image, mime encoded in an e-mail attachment, would be split into many small packets. Each packet is numbered and may be routed thru different paths across the net. They may very well arrive out of order. That's why they are numbered. At the receiving end, packets are correctly reordered, and the e-mail client will eventually get the mime encoded attachment in one big chunk as the sender intended it.

Why on earth would it help you, to do the same once *again* on top of that?

---

(*Earth to David*: just answer the poor guys question instead of lecturing him. *David*: no!)

---

### Post by mike555 on 2012-07-02
I just use 7zip , it lets you split and password protect......in Ubuntu you want to install "p7zip-full" .......  in Windows ,if you don't already have it install "7zip"......

---

### Post by sudodus on 2012-07-02
In my Ubuntu 10.04 LTS ***split*** is already there. No need to install it.

```
man split
```

Using the attached file from post # 24 I made this example.

```
split -b 10k how-to-get-password.png
cat xa* > x.png
diff how-to-get-password.png x.png
ls -l how-to-get-password.png xa* x.png
```

Just for fun. Not that it improves the security compared to encryption.

Typically you split files because the file system or the storage media cannot handle big files.

---

### Post by 3dmatrix on 2012-07-02
> **oldsoundguy said:**
> This all looks like a whole bunch of work to accomplish what could be done by uploading your file to a personal web space as provided by your ISP and just sending the recipient the link to the file and let them download it.  Then, once the file has been downloaded .. delete it.

No my dear friend in many cases even if you delet it, it actually does not gets deleted.
I have read about such things happening on Facebook and Flicker so it could happen on any server :)

[http://news.cnet.com/8301-1023_3-57371965-93/facebook-photos-deleted-today-still-there-tomorrow/](http://news.cnet.com/8301-1023_3-57371965-93/facebook-photos-deleted-today-still-there-tomorrow/)

[http://www.pcmag.com/article2/0,2817,2399914,00.asp](http://www.pcmag.com/article2/0,2817,2399914,00.asp)

[http://www.flickr.com/help/forum/en-us/72157625577805066/](http://www.flickr.com/help/forum/en-us/72157625577805066/)

[http://www.flickr.com/help/forum/en-us/72157625717729499/](http://www.flickr.com/help/forum/en-us/72157625717729499/)

You never know they might be having many mechanism to recover it. And they always keep backup of users files.

---

### Post by 3dmatrix on 2012-07-02
> **David Andersson said:**
> The *Internet* does that for you *totally automatically*. Any data, file or e-mail is split into packets, normally of size about between 1 or 2 kilobytes (I think). An image, mime encoded in an e-mail attachment, would be split into many small packets. Each packet is numbered and may be routed thru different paths across the net. They may very well arrive out of order. That's why they are numbered. At the receiving end, packets are correctly reordered, and the e-mail client will eventually get the mime encoded attachment in one big chunk as the sender intended it.

Why on earth would it help you, to do the same once *again* on top of that?

---

(*Earth to David*: just answer the poor guys question instead of lecturing him. *David*: no!)


I do not find keeping sensetive data on any server very reliable. I would not even keep it on any computer that is online. Forget email it :) because you never know who all have access to your data on the server.

---

### Post by 3dmatrix on 2012-07-02
Say . . . I write a letter (on paper) in a coded language (encryption), which only A (me) and B (destination) know. Then cut that paper in 4 (or more) pieces and send 1 piece by any courier service, 1 by postal service, 1 piece through a friend of mine and 1 i carry myself to B.

In such a case, even if there is anyone genius enough to be able to decipher the coded language. Which might be difficult but not impossible :) i do not need to worry as the decoded letter will still be incomplete.

I often read / hear people getting stressed that they lost their usb drive / dvd / external hdd / laptop / mobile with some very important data in it. Or it suddenly stopped working and they are afraid in taking it to any place to get repaired as they are worried abt the safety / security of (some specific) files inside. Or they are afraid of emailing / keeping on servers due to apparant risk envolved. So if i encrypt and split such 1 or 2 very important files in to multiple pieces and keep it / send through different medium then i do not need to worry as anyway the file is incomplete.

Try to realize my dear friends, due to what ever reason, i have to live in a place these days which is not very well known for this kind of security.

.

---

### Post by HermanAB on 2012-07-03
$ man gpg 
$ man split
$ man cat
$ man tar

---

### Post by 3dmatrix on 2012-07-03
> **HermanAB said:**
> $ man gpg 
$ man split
$ man cat
$ man tar

Thanx !

---

### Post by Rick.B9 on 2012-07-03
I think since you're going to deliver the files separately by different media, then you'll be served well by 7zip (p7zip-full package.)  

Other than that, you might split the files with 7zip and put the compressed archives into different encrypted containers using enc_fs.  Enc_fs also has a gui interface available called cryptkeeper, although it's easy enough on the command line.  Last option would be the same as above, but put the archives into TrueCrypt containers.  Deliver the password using gpg key authentification.

---

### Post by sudodus on 2012-07-03
> **3dmatrix said:**
> 
Try to realize my dear friends, due to what ever reason, i have to live in a place these days which is not very well known for this kind of security.

I see. Maybe that is why you could not open the link in post #20. 

There might be a reason to avoid typical encrypted file formats and send something home-made, that does not look interesting.

---

### Post by 3dmatrix on 2012-07-03
> **sudodus said:**
> I see. Maybe that is why you could not open the link in post #20. 

There might be a reason to avoid typical encrypted file formats and send something home-made, that does not look interesting.

You are right

I did not find 7zip in synaptic. Where is it awailable ?

---

### Post by sudodus on 2012-07-03
> **3dmatrix said:**
> You are right

I did not find 7zip in synaptic. Where is it awailable ?
```
sudo apt-get install 7z
```

See also [[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=2014689_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2014689")

---

### Post by David Andersson on 2012-07-03
> **3dmatrix said:**
> 
[QUOTE=David Andersson]
[QUOTE=3dmatrix]
 and then splitting the file and transporting them to the destination through multiple routes and then will be joined and decripted back at the destination.

The *Internet* does that for you *totally automatically*.
[/QUOTE]
Forget email it :) because you never know who all have access to your data on the server.[/QUOTE]
Don't get stuck on that the example is e-mail. You'll transfer the file over the Internet, right? Then it doesn't matter if it's e-mail, ftp, http, whatever. The file will be **split** into pieces and then put together again at the receiver, just as you want.

[QUOTE=3dmatrix] then i do not need to worry as anyway the file is incomplete.[/QUOTE]
You should trust the encryption. If you think your adversary can break it, it does not matter if they will only see a part of it or the whole picture (or a fraction of your mails or all of them). If it is the mafia or the secret police, they won't abide to "reasonable doubt". They will act on a partial picture.

One might think that encrypting the file *twice*, with two *different crypto* algorithms, and two *different keys*, would make it much harder to break. And sometimes it is. Maybe that could ease your mind. (But I think encrypting once, with a really good algorithm, and a really long key, is generally better.)

With most crypto, the real danger is not that it would be broken. The real danger is that spyware in your friend's computer (or in your's) will snatch the password from the keyboard, or will copy the file after it is decrypted (or before it is encryped). (E.g. Vietnam Gov is spying on dissidents via trojan in keyboard driver [http://www.eweek.com/c/a/Security/Google-Malware-Attacks-Target-Vietnam-Dissidents-498247/](http://www.eweek.com/c/a/Security/Google-Malware-Attacks-Target-Vietnam-Dissidents-498247/).)

[QUOTE=3dmatrix] i have to live in a place these days which is not very well known for this kind of security.[/QUOTE]
Then it is important to use proven security measures.

---

### Post by David Andersson on 2012-07-03
I am thinking, maybe what you are after, is a way to hide the fact that secret information exists at all. That is called *Stegography* (WP article [http://en.wikipedia.org/wiki/Steganography](http://en.wikipedia.org/wiki/Steganography) where they have an example image of a tree which hides an image of a cat.) It is not only that you can hide images in images, or sounds in sound files. You can hide any data inside a set of different file types (images, sound files, or document files, amongst other things). An encrypted partition also provides opportunity to hide data. It can be made to just look like an unused partition with random bytes in it. Or you can hide data in unused blocks in your file system. (It requires special tools, that you'll have to hide too.)

---

### Post by sudodus on 2012-07-03
> **David Andersson said:**
> I am thinking, maybe what you are after, is a way to hide the fact that secret information exists at all. That is called *Stegography* (WP article [http://en.wikipedia.org/wiki/Steganography](http://en.wikipedia.org/wiki/Steganography) where they have an example image of a tree which hides an image of a cat.) It is not only that you can hide images in images, or sounds in sound files. You can hide any data inside a set of different file types (images, sound files, or document files, amongst other things). An encrypted partition also provides opportunity to hide data. It can be made to just look like an unused partition with random bytes in it. Or you can hide data in unused blocks in your file system. (It requires special tools, that you'll have to hide too.)

Interesting!

---

### Post by 3dmatrix on 2012-07-03
> **David Andersson said:**
> I am thinking, maybe what you are after, is a way to hide the fact that secret information exists at all. That is called *Stegography* (WP article [http://en.wikipedia.org/wiki/Steganography](http://en.wikipedia.org/wiki/Steganography) where they have an example image of a tree which hides an image of a cat.) It is not only that you can hide images in images, or sounds in sound files. You can hide any data inside a set of different file types (images, sound files, or document files, amongst other things). An encrypted partition also provides opportunity to hide data. It can be made to just look like an unused partition with random bytes in it. Or you can hide data in unused blocks in your file system. (It requires special tools, that you'll have to hide too.)

Hmmmmm ! Thats nice :)

---


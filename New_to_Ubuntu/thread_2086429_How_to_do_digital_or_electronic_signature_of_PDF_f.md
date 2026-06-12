---
title: "How to do digital or electronic signature of PDF file to guarantee authenticity"
date: 2012-11-20
forum: New to Ubuntu
---

### Post by swarup on 2012-11-20
I need to create some pdf files which will be either tamper proof or will have a digital/electronic signature which verifies authenticity. What is the best approach for this in Ubuntu? (It should be something by which common non-technical people can easily verify authenticity.)

---

### Post by coldcritter64 on 2012-11-20
md5sums are one method, one bit in the file changes and so will the md5sum. It is easy enough to use (though it is a terminal application).

Look up gtk-hash with synaptic or USC, for a front end for md5sum etc.

Using md5sum in terminal,

```
md5sum </path/to/file/and/filename.ext>
```copy the md5sum the terminal gives out and send it as a txt file (or post the md5 to a site) with the original file.  Any alterations to the original file will cause a mismatch with the md5 checksum you distribute, when the receiver of the file does the same check.

I personally found the gui and usage for gtk-hash unintuitive, and refer back to the terminal method with md5sum and copying/pasting from the terminal as the easiest/quickest method here. You may find gtk-hash useful though.

---

### Post by swarup on 2012-11-21
Wonderful-- that seems incredibly easy. So I just ran md5sum for a pdf file on my desktop, and got this output in the terminal window: 

70eb41f67944e2e64e99371f74ff4ada

So I would include the above in a text file with my pdf document. And anyone could run md5sum to check and see if they get the same code as I pasted above. Is that all there is to it?

Two questions about this:

1. Can md5sum be run by anyone regardless of operating system? That is, is this md5sum a standard and simple operation in windows and OSX as well? I would be sending this file to non-technical users, and would need to instruct them in how to get the md5sum in their OS.

2. When folks put a "digital signature" or an "electronic signature" on their document, does it do the same job as the md5sum? Or better or worse in any regard?

---

### Post by Lars Noodén on 2012-11-21
An MD5 checksum can be made by users on most, if not all, systems.  I don't know about Windows, but all the others have it built-in.  MD5 can help guarantee integrity of the file but not authenticity.  Even so, it might be better to use SHA2 via sha256sum, since it is now feasible to generate MD5 collisions with common hardware.

A digital signature is quite different and is used to try to guarantee the authenticity and possibly help with non-repudiation.  For digital signatures see the standard PGP and the utility GnuPG.

---

### Post by coldcritter64 on 2012-11-21
> So I would include the above in a text file with my pdf document. And  anyone could run md5sum to check and see if they get the same code as I  pasted above. Is that all there is to it?Yes. It checks the integrity of the file. Not who the sender is though, ie, it is not a digital signature.

1. md5sum is available for Windows, but has to be downloaded and added to the system by the user. [[COLOR=Blue]Some info[/COLOR]]("http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows") - from linuxquestions.org. (note: the link includes a download link in the first post for md5sum.exe) Apparently, there is a native Win method according to the first reply :).

2. See Lars Noodén's explantion and comments. post 4

---

### Post by swarup on 2012-11-21
Ok, many thanks to both of you for that information. :P 

Regarding md5sum, Lars has said it is used to confirm the "integrity" of a file. And coldcritter64 has said it is used to confirm the "validity" of a file. It is not clear for me yet what is the difference between integrity, validity, and authenticity.

Here is the scenario I'll use it for: I'll send a pdf file to say, 500 people. And they may circulate it among another 500 more. My desire is that there should be a way for these 1000 people to confirm whether the pdf file they have is an untampered, unadulterated copy i.e. identical to what I have originally sent or not. 

The pdf file I am sending is a text file, and not any sort of program. So unlike when one downloads say Ubuntu 12.10 and wants to know if it is valid, there isn't any question in my pdf file of "functionality as a program", because it is just a text file. My need is for people to be able to confirm what they have is identical to what I originally sent. 

So if the md5sum output they get matches the one I have published, does that do the trick? Or is rather a digital signature needed for this instead?

---

### Post by coldcritter64 on 2012-11-21
md5sums will verify if a file has been altered since the time you ran the original command, so any of your recipients would be able to use it. The md5sum is unique to that file and if 1 bit in the file contents changes so does the md5sum.

Digital signatures will verify to a recipient that YOU sent that file  (read this as "authenticity"), I don't know if a digital signature will verify contents (though I suspect it will). I will need to defer to other helpers with regards to pgp/gpg and digital signatures.

Please note I edited my post to use "integrity" as validity could be confusing (validity could refer to digital signatures or md5sums). This was to bring my terminology into line with Lars's post. Sorry if that caused any confusion. Cheers, coldcritter64.

---

### Post by swarup on 2012-11-21
I see. Well, I am really not concerned that they confirm that I sent it. My concern is that it can be confirmed that it is unchanged. From reading on the web it seems that a digital signature does achieve this as well i.e. confirms the file to be unchanged. If the md5sum is easier for recipients of my pdf to use, then it sounds like that should be sufficient. 

It should be kept in mind though that the vast majority of recipients will be Windows users, so the md5sum needs to be easy for them to use. I'll check out the info you sent in your second post, and see how easy it seems for Windows users. Otherwise my guess is that for Windows users there is probably some other method which is typically used by them...

---

### Post by Lars Noodén on 2012-11-22
Validity often refers to adherence to a particular syntax or data format, for example, like instances of SGML or XML like HTMl4 or XHTML.  You can [validate XHTML, HTML](http://validator.w3.org/) or CSS using the W3C's validator.  Other DTDs like Docbook or TEI-lite can also be validated to make sure they conform to the rules.  

Integrity is just whether or not the message has changed since it was written or sent.  Checksums like MD5 and SHA can help with that.  MD5 has been used for along time, but should be phased out.  SHA would be better than MD5 since it is now [feasible to generate MD5 collisions](http://www.forbes.com/sites/richardstiennon/2012/06/14/flames-md5-collision-is-the-most-worrisome-security-discovery-of-2012/) with regular equipment.  For casual downloads, MD5 might be adequate to ensure that the file downloaded whole and unchanged.  But in principle it would be best to wean people off MD5 and get them using SHA.

---

### Post by CaptainMark on 2012-11-22
To put Lars' comment in more laymen terms some people can alter a file without changing the MD5 hash so although MD5SUM is a good way of a checking a file hasn't 'accidentally' corrupted when downloading from the internet it is not a fool-proof way of knowing that someone hasn't tampered with or sabotaged your file.

An easier way would be to host the file on a file-sharing service like Dropbox or Ubuntu-One and just share the link between all of these people, anyone can share the link address with anyone else and they will all be downloading it directly from your original copy, making it safe enough for most purposes

---

### Post by swarup on 2012-11-22
I just tried sha256sum, and it seems to work exactly the same way as md5sum, a piece of cake. At least in Ubuntu. But it has to be easily available across operating systems, i.e. in Windows and OSX. Is that the case?

CaptainMark, your suggestion about using a filesharing site is interesting, and I will think about using that. But my initial feeling is that only using this may not be sufficient for me, as I still want people to be able to know that if someone else passed it to them they can confirm its integrity. 

If someone wants to have some kind of mark of integrity for a pdf text file which is easily utilizable across operating systems, is there something common and easy out there? Would sha256sum be the tool for the job?

---


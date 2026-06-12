---
title: "[SOLVED] How to encrypt a java .dat"
date: 2008-06-03
forum: Programming Talk
---

### Post by psychok7 on 2008-06-03
hi there guys.. im working on a password manager(just for fun) in java. Right now im saving my files in .dat but i know thats not enough so secure my data, so my question is how do i encrypt my saved files? is it like a package that im suposed to import??

---

### Post by Zugzwang on 2008-06-03
Use Google for search for "Java" and "encryption".

---

### Post by psychok7 on 2008-06-03
> **Zugzwang said:**
> Use Google for search for "Java" and "encryption".

yeah i did try that..a little bit complicated for my programming knowledge.. need something easier to understand

---

### Post by xlinuks on 2008-06-03
".dat" doesn't make your file/data encrypted, it's just the extension of the file.
The "encryption" issue is complicated, it's worth spending some time on it, I guess one can't learn it in a few minutes. On the flip side the people who know well how to secure a system afaik are paid very well.

---

### Post by NormR2 on 2008-06-03
How well do you want your data to be secured? The fancy encryption code you saw on google would keep out most everyone. If you only want to prevent someone from reading the .dat file with a text editor, you could build your own simple encryption/encoding decryptioin/decoding methods. That would at least require a programmer to write code to look at your data.  
You would get some programming experience in the process and if you designed your classes/methods properly, you could eventually replace your code with more professional code when the need arises.

---

### Post by psychok7 on 2008-06-03
> **NormR2 said:**
> How well do you want your data to be secured? The fancy encryption code you saw on google would keep out most everyone. If you only want to prevent someone from reading the .dat file with a text editor, you could build your own simple encryption/encoding decryptioin/decoding methods. That would at least require a programmer to write code to look at your data.  
You would get some programming experience in the process and if you designed your classes/methods properly, you could eventually replace your code with more professional code when the need arises.

thats actualy a very good idea :) thanks dude.. i remember i wrote an encryption/decryiption code for school last year but nothing that powerful, only putting each character=to 2 ahead.. but not a bad idea at all for a person who doesnt want to waist a lot of time with that ;) thanks

---

### Post by GeekLove_JavaStyle on 2009-10-02
I'm about a year late, but try:
[http://www.jasypt.org/cli.html](http://www.jasypt.org/cli.html)

I'm doing Java encryption right now and it helps greatly.  

I'm using:
[http://www.jasypt.org/bouncy-castle.html](http://www.jasypt.org/bouncy-castle.html)

---

### Post by credobyte on 2009-10-02
[http://www.twmacinta.com/myjava/fast_md5.php](http://www.twmacinta.com/myjava/fast_md5.php) - assuming that you do it for fun, I think you'll be fine with this.

---

### Post by cariboo on 2009-10-02
Thread necromancy. This thread is closed.

---


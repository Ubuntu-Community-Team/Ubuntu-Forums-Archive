---
title: "Perl unpack"
date: 2011-06-10
forum: Programming Talk
---

### Post by Sahan J on 2011-06-10
Hi, I'm a complete newbie at perl and I require an explanation on what the following piece of code does. Thank you in advance.

$t = test(10);  

 sub test() {
   my $str = unpack("B32", pack("N",shift)); 
  $str2 = substr($str,16,length($str)); 
  return $str2; 
}

---

### Post by nzjethro on 2011-06-10
I've never come across the unpack method, but this may help:

[http://www.tutorialspoint.com/perl/perl_unpack.htm](http://www.tutorialspoint.com/perl/perl_unpack.htm)

What in particular about the code do you not understand?

---

### Post by Sahan J on 2011-06-10
> **nzjethro said:**
> 
What in particular about the code do you not understand?


Every thing about it in fact.. I'm a Java developer and PERL is alien to me. I've been trying to decipher this code using online resources but still I'm not sure of the exact output.

---

### Post by slavik on 2011-06-10
converts an item into network order, then returns what it looks like in bits ...

---


---
title: "std::string"
date: 2006-08-19
forum: Programming Talk
---

### Post by Kurt` on 2006-08-19
Hi,

All my life I've been using char * for string data. I've always been careful about range-checking and verifying user-inputted data before using sprintf, strcpy, etc.

I've recently started using std::string. Are there any reasons why I SHOULDN'T or things to look out for when using it?

Thanks

---

### Post by thumper on 2006-08-20
Some people complain about "performance" for some arbitrary definition of "performance" with regard to std::string.  But in all my experience, for the domain that I work in, there has never been any problems with using std::string.

The only thing I'd say to look out for is the difference between the **data** and **c_str** methods.  This bites some people, specifically those coming from a RogueWave background where the RWString::data method has the same effect as std::string::c_str.

But the guts is: use it.  Never use fixed sized char buffers if you can avoid it.

---

### Post by bonefry on 2006-08-20
Both char* and std::string suck when it comes to internationalization.

I use GtkString contained by GLib.

---


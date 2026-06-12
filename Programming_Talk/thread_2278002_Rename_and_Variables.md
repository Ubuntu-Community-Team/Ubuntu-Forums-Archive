---
title: "Rename and Variables"
date: 2015-05-13
forum: Programming Talk
---

### Post by GrouchyGaijin on 2015-05-13
Rename and Variables

I was playing with rename today and thought I'd like to rename 
```
 Camera Roll.zip 
``` to ```
 Camera-Roll.zip 
```

(I know there are easier ways to do this. but the idea is to practice using rename.)

```
 rename 's/Camera Roll/Camera-Roll/' *.zip 
``` worked.

So I thought how about adding the date to the end of the new file name, before the extension.
In the terminal I set:
```
now=$(date +"%d-%b-%Y") 
```

Then I tried:
```
 rename 's/Camera-Roll/Camera-Roll-"$now"/' *.zip 
```

This gives me the error:
```
 Global symbol "$now" requires explicit package name at (eval 1) line 1. 
```

However, if I avoid rename and simply use:
```
 mv Camera-Roll.zip Camera-Roll-"$now".zip 
```

I get the desired result: ```
 Camera-Roll-13-May-2015.zip 
```

Could someone please exaplian:
1. What does Global symbol "$now" requires explicit package name at (eval 1) line 1. actually mean?
2. Is it possible to use variables, like the date varaible with the rename command?  If so, how should I change my command?

---

### Post by sisco311 on 2015-05-13
> **GrouchyGaijin said:**
> 
Could someone please exaplian:
1. What does Global symbol "$now" requires explicit package name at (eval 1) line 1. actually mean?


It's a Perl error.

(In Ubuntu) the rename command is a Perl script and in the terminal emulator you are using  Bash. The single quotes you used in your command are preventing Bash to perform the parameter expansion.  Please see: [http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)

> **GrouchyGaijin said:**
> 
2. Is it possible to use variables, like the date varaible with the rename command?  If so, how should I change my command?

Yes it is; use the proper quotes. ;)
If you have any  further questions, please don't hesitate to ask.

---

### Post by Lars Noodén on 2015-05-13
*rename* is a perl script.  By passing it a literal string '$now', the perl interpreter is parsing it to be a perl variable.  In that case it is a variable that has not yet been defined.  

About the quotes, the shell uses single quotes for things to take literally.  Things in double quotes will be processed first and variables in there expanded.  So the following will give you what you are trying for:

```

 rename "s/Camera-Roll/Camera-Roll-$now/" *.zip

```

But you might want *now=$(date +"%F")* instead.  That will sort better.

---

### Post by GrouchyGaijin on 2015-05-13
Thank you Lars!  Your explanation is very easy to understand.

---


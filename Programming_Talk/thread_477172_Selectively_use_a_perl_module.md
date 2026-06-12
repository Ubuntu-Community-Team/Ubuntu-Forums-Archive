---
title: "Selectively use a perl module?"
date: 2007-06-18
forum: Programming Talk
---

### Post by tr333 on 2007-06-18
Hi,

Is it possible to selectively use a perl module, based on whether it is installed on the system?

eg:
```

# based on the Digest::SHA module
my $use_digest_sha = 0;
if (DIGEST_SHA_MODULE_EXISTS) {
    use Digest::SHA;
    $use_digest_sha = 1;
}

if ($use_digest_sha) {
    # code here that uses the Digest::SHA module
} else {
    # continue without using the Digest::SHA module
}

```

---

### Post by j1n3l0 on 2007-06-18
Hi,

From my very limited knowledge of Perl, I can tell you that piece of code will not work. Essentially because Perl evaluates your 'use Module' at compile time ... before your 'if' statement is processed at runtime. So if the module is not installed you get a 'Can't find Module in @INC' error message.

One way you may try is to have the body of the if statement (that uses your Module) and the else block (that does not use the Module) in separate scripts. That way your main script can check for the Module in @INC. If it finds it, call the script that uses it, else call the script that doesn't need it! :D

```
# search for the module (perhaps using File::Find)
my $found = find_module();
if ($found) {
   qx(./script_with_module.pl);
}
else {
   qx(./script_without_module.pl);
}
```
Hope that makes sense

Ps: You would have to write the find_module() subroutine yourself ;)

---

### Post by tr333 on 2007-06-18
thanks for the tip!
i don't like using wrapper scripts, but if there's no other way to do this then i guess it has to be done.
i would have thought something like this would be built-in to perl :?

---

### Post by Mr. C. on 2007-06-18
do this:

```
eval { require Digest::SHA; };
my $hasDigestSHA = $@ ? 0 : 1;

```
MrC

---

### Post by tr333 on 2007-06-18
> **Mr. C. said:**
> do this:

```
eval { require use Digest::SHA; };
my $hasDigestSHA = $@ ? 0 : 1;

```
MrC

It gave me an error about having the "use" in there, so i removed the "use" keyword and it seems to be working :D

thanks!

```
eval { require Digest::SHA; };
my $hasDigestSHA = $@ ? 0 : 1;
```

---

### Post by Mr. C. on 2007-06-18
And well it should.  It was my copy/paste typo, sorry.  I've corrected my original text.

MrC

---


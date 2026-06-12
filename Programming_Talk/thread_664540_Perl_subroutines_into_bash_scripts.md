---
title: "Perl subroutines into bash scripts"
date: 2008-01-11
forum: Programming Talk
---

### Post by flightless bird on 2008-01-11
Just a quick question from a total self-taught noob - I have just written my first program, a bash script, (hooray) which happens to depend on a couple of perl scripts. I was wondering if it is possible to incorporate the perl scripts as subroutines into the bash script or if that just doesn't get done :)

Cheers

---

### Post by Vixis on 2008-01-11
something like this:
[http://tldp.org/LDP/abs/html/wrapper.html#EX56](http://tldp.org/LDP/abs/html/wrapper.html#EX56)

---

### Post by KCPokes on 2008-01-11
A shell script can essentially call any program, given that you make the call correctly.  That's the beauty of shell scripts.  Just keep in mind that you'll need to perform due diligence on the completion status of those scripts.  Most on failure return a code other then zero, but that is not always 100% the case.  This means that if your perl job fails and you do not handle the return status correctly, the calling shell script will continue to execute.  Most cases this is not the desired action; if any part fails, you normally want to exit.  

To call the script, use fully qualified paths.  For example, depending on where your perl is installed, you'd call it as:

```

/usr/bin/perl <perlJob.pl>

```

[EDIT]  
I'd call the Perl jobs as external scripts, rather then embedding them, but its just a preference.  You can approach it however you feel most comfortable.

---

### Post by flightless bird on 2008-01-11
I can see how that works for single lines of perl, how does one go about calling a whole script embedded within the same file? In the second example found on the link given by Vixis I can't see how the two parts of the script interact, and while it's nice to know KCPokes that others consider it good form to do as I have been doing and call external scripts, I would like to know how you would format and call internal ones.

---


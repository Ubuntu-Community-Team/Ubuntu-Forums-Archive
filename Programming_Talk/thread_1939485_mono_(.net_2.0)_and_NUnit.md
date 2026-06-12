---
title: "mono (.net 2.0) and NUnit"
date: 2012-03-11
forum: Programming Talk
---

### Post by robwilkens on 2012-03-11
I was noticing the NUnit for .net 2.0 no longer appears to be available in Ubuntu precise.  It was there in Ubuntu 10.04.  

Here's how I discovered this:
From Monodevelop in Ubuntu 10.04:
Create a new test project (type C#, gtk-sharp)
Go to project settings (Project Menu)
Go to General settings and set runtime version to MONO/.NET 2.0
Click OK
From project menu, click edit references
Scroll down, and if nunit is installed you'll see things like nunit.core and nunit.framework

Then:
From Monodevelop in Ubuntu Precise (beta)
Create a new test project, same settings
Set it to .net 2.0 as before
Go to edit references
Scroll down, and you won't see any nunit references alphabetically.

There does not seem to be a way to add any packages with this..  I noticed if i "apt-cache search libnunit" there's a version 2.4-cil in 10.04 and version 2.5-cil in precise-- is it possible that somewhere along the line someone decided that including the .net 2.0 version was no longer important?

This is not 100% important, as i think i can download the binary and try to figure out how to make it work from the nunit website, but was there a reason this was removed from ubuntu precise?

-Rob

---

### Post by directhex on 2012-03-11
> **robwilkens said:**
> is it possible that somewhere along the line someone decided that including the .net 2.0 version was no longer important?

Ubuntu 11.10 and higher only fully supports 4.0 profile - 2.0 support is deprecated in these releases.

---

### Post by robwilkens on 2012-03-11
> **robwilkens said:**
> 
From Monodevelop in Ubuntu 10.04:
From Monodevelop in Ubuntu Precise (beta)
blah blah blah

-Rob

I wrote the above....

But when I built monodevelop from the latest monodevelop source, my problem i reported here went away...  I still have other problems relating to compiling what i want to compile, but i think it'll be more appropriate to first try to solve them myself, then if i have issues ask at the monodevelop mailing list.

=and thanks to original reply for telling me .net 2.0 profile not supported on ubuntu, it's just unfortunate that monodevelop offers it as an option, and i downloaded that from the ubuntu software center...

-Rob

---

### Post by directhex on 2012-03-12
> **robwilkens said:**
> I wrote the above....

But when I built monodevelop from the latest monodevelop source, my problem i reported here went away...  I still have other problems relating to compiling what i want to compile, but i think it'll be more appropriate to first try to solve them myself, then if i have issues ask at the monodevelop mailing list.

=and thanks to original reply for telling me .net 2.0 profile not supported on ubuntu, it's just unfortunate that monodevelop offers it as an option, and i downloaded that from the ubuntu software center...

-Rob

It works for some limited contexts (i.e. if you only use namespaces provided in the Mono source, such as WinForms, but nothing outside like GTK#)

---


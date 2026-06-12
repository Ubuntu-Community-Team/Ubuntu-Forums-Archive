---
title: "Monodevelop + Winforms"
date: 2007-06-08
forum: Programming Talk
---

### Post by csixx on 2007-06-08
I'm using monodevelop (.12) on Fiesty. According to the monodevelop website, winforms support is a standard (included) part of monodevelop.

I see no way, with my installed version to create a winforms application.

putting:
using System.Windows.Forms;
in my code fails (missing reference?)

I've looked in the references section, and see nothing that looks to be winforms..
Is there a dll I need to download from someplace to support this? The monodevelop site tells me I already have this ability and therefore there is nothing to download.

I've tried using the Gtk forms, but the differences are significant and documentation is really lacking.
For example, I coulden't find any help on overriding the OnPaint method so that I could do some drawing on the form surface.

Can anyone shed some light on this for me?

---

### Post by luisromangz on 2007-06-08
Hi, I was using Monodevelop when I saw your post ;)

When I click on the project's References editor, I can add the System.Windows.Forms reference. Maybe it's missing because you hadn't installed it. The packages are called libmono-winformsX.0-cli, where X is 1 or 2 depending on what version of ".net" framework you are targeting.

By the way, Gtk# is way better than Winforms, speaking about functionality and cross plataform support. I agree with you in that WinForms has a way better documentation, but it still rules. In Gtk#, the Paint event is called Expose ;)

I suggest you to use the Monodevelop 0.13 version from SVN, as it has many more features than 0.12 (and default 0.13).

Bye!

---

### Post by csixx on 2007-06-08
Thanks for your help... 

I downloaded that package and the package manager tells me its already installed.
Monodevelop must be ignoring it for some reason.

I found it in /usr/lib/mono/gac/System.Windows.Forms/2.0.0.0__b77a5c561934e089 so I am able to add a reference to it now by browsing to it (monodev still doesn't have it in the ref list)

---

### Post by csixx on 2007-06-08
Ok, this is pretty frustrating.

Added the reference, tried to compile a "hello world" winforms app.

compiler pukes:

** (/usr/lib/mono/1.0/mcs.exe:7611): WARNING **: Missing method .ctor in assembly /usr/lib/mono/gac/System.Windows.Forms/2.0.0.0__b77a5c561934e089/System.Windows.Forms.dll, type System.ComponentModel.InitializationEventAttribute

** ERROR **: Can't find custom attr constructor image: /usr/lib/mono/gac/System.Windows.Forms/2.0.0.0__b77a5c561934e089/System.Windows.Forms.dll mtoken: 0x0a00060b
aborting...

---

### Post by xanium4332 on 2007-06-14
Just found this thread, I have the exact same problem. Both monodevelop and WinForms have been installed from the Ubuntu repos, but WinForms just doesn't show up in the list of references. Anybody have any ideas?

Thanks, James

---

### Post by gwi on 2007-07-18
Unfortunately Monodevelop does not use the GAC. If you want an assembly that is in the GAC to show up in the pakages tab, you should create a package config file in /usr/lib/pkgconfig. You can use one of the existing files as a starting point (as I did).

Here are the contents of my /usr/lib/pkgconfig/windows-forms.pc:
```
prefix=${pcfiledir}/../..
exec_prefix=${pcfiledir}/../..
libdir=${prefix}/lib
includedir=${prefix}/include

Name: System.Windows.Forms
Description: Windows Forms for Mono
Version: 2.0.0.0
Libs: -r:${prefix}/lib/mono/2.0/System.Windows.Forms.dll
```

(thanks to lluis on the #monodevelop channel @ icr.gimp.org for helping me out)

I also get the same "Missing method .ctor in assembly" error though...

---

### Post by hughdoar on 2008-02-25
This patch worked for me, thanks, but yes, the same error.

---

### Post by rba1988 on 2008-05-31
Have you tried using it in 8.10? Everything works perfect for me. I even got the Winforms Designer to work. I needed these stuff for .NET development on Linux so I can work with C# without ever having to touch Windoze...;)

Here are the stuff I installed with apt-get:
mono-gmcs
mono-winforms*

Then I installed winforms designer by following the instructions <a href = "http://www.mono-project.com/WinForms_Designer">here</a>.

---

### Post by Number6 on 2008-06-09
I was having this issue but that second post gave me the clue.. In MonoDevelop, if you right click the "References" folder in the solution browser on the left and choose "Edit References" you can add the "System.Windows.Forms" reference. Then my WinForms program compiled sweet

---

### Post by toastmaker on 2008-06-26
Hello,

I've checked up that you have successfully installed winforms designer under Mono on Hardy 8.04 in this post. May I beg for few more details, please? Did you use standard Hardy repositories and extra downloaded just the Mono Winforms Designer using subversion as it is at this link [http://www.mono-project.com/WinForms_Designer](http://www.mono-project.com/WinForms_Designer) ? Did you need to have installed the whole Mono SVN trunk? Or only the designer part

```
svn co svn://anonsvn.mono-project.com/source/trunk/mwf-designer
make; make run
```

is enough?

Martin

---

### Post by why2jjj on 2008-07-18
> **toastmaker said:**
> Hello,

I've checked up that you have successfully installed winforms designer under Mono on Hardy 8.04 in this post. May I beg for few more details, please? Did you use standard Hardy repositories and extra downloaded just the Mono Winforms Designer using subversion as it is at this link [http://www.mono-project.com/WinForms_Designer](http://www.mono-project.com/WinForms_Designer) ? Did you need to have installed the whole Mono SVN trunk? Or only the designer part

```
svn co svn://anonsvn.mono-project.com/source/trunk/mwf-designer
make; make run
```

is enough?

Martin


Hi:

It looks like I am having the same problem as other people on here.

I am using Ubuntu 8.04, 64-bit.  I installed everything there is available to mono, including libmono-winforms*, using Synaptic Package Manager.  Partial apt-get output is as follows:

i   libmono-system2.0-cil           - Mono System libraries (2.0)               
i   libmono-system2.1-cil           - Mono System libraries (2.1)               
i   libmono-winforms1.0-cil         - Mono System.Windows.Forms library         
i A libmono-winforms2.0-cil         - Mono System.Windows.Forms library         
p   libmono-zeroconf1.0-cil         - CLI library for multicast DNS service disc
i   libmono0                        - libraries for the Mono JIT                
p   libmono0-dbg                    - libraries for the Mono JIT, debugging symb
i   libmono1.0-cil                  - Mono libraries (1.0)                      
i   libmono2.0-cil                  - Mono libraries (2.0)           


The places the download manager looking for packages include all the ubuntu defaults:

us.archive.ubuntu.com/main
.../multiverse
.../restricted
.../universe

and Monodevelop does not recognize System.Windows.Forms anywhere- in help or when I type in System.Windows.Forms in a .cs file in the Monodevelop editor.

I thought I saw one possible fix to this was to uninstall mono everything then re-install, but that does not make much sense to me.  is the solution by hacking /usr/lib/pkgconfig/windows-forms.pc which was shown earlier the right fix?

Thanks for the help!

---

### Post by true_friend on 2008-07-20
It is better to use Gtk#. Mono winforms implementation is so much buggy and untrustable.

---

### Post by why2jjj on 2008-07-20
> **true_friend said:**
> It is better to use Gtk#. Mono winforms implementation is so much buggy and untrustable.

I am in a Microsoft-shop so Winforms is very much attractive for C# apps already written for Microsoft platforms, even if basic functionality can work, and GTK# is not much of an option.

(Java would be a better solution for this portability work but my company is not that open-minded yet).

---

### Post by lakersforce on 2008-08-10
> **toastmaker said:**
> Hello,

I've checked up that you have successfully installed winforms designer under Mono on Hardy 8.04 in this post. May I beg for few more details, please? Did you use standard Hardy repositories and extra downloaded just the Mono Winforms Designer using subversion as it is at this link [http://www.mono-project.com/WinForms_Designer](http://www.mono-project.com/WinForms_Designer) ? Did you need to have installed the whole Mono SVN trunk? Or only the designer part

```
svn co svn://anonsvn.mono-project.com/source/trunk/mwf-designer
make; make run
```

is enough?

Martin

Yes, we beg for a few more details!!

---

### Post by alimooghashang on 2010-02-10
Hi
could you please tell me that how to use this designer?
thanks

---


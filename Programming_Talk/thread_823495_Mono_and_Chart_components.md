---
title: "Mono and Chart components"
date: 2008-06-09
forum: Programming Talk
---

### Post by franaria on 2008-06-09
After much searching on the network finally I found the components for Mono I was looking for. 
The problem is that on my UBUNTU 8.04 I can't compile (probably the file. / Config that comes with the component is not compatible with my distro because of some variable environment.) 
Now kindly a user of the mono-project's forum (Eric) has compiled it for me with a Mandriva Spring but I want to compile it with my UBUNTU. 
Is there anyone who can give me a hand? 

The component is here: 
[http://www.medsphere.org/projects/widgets]("http://www.medsphere.org/projects/widgets") 

and the post to which I refer is here: 
[http://www.nabble.com/Graph-widgets-to17646571.html]("http://www.nabble.com/Graph-widgets-to17646571.html") 

I mean if someone can compile it with a Mandriva Then I can do it with UBUNTU ? 
 
This is a screeshot of the components at work: 
[http://www.nabble.com/file/p17729256/Schermata.png]("http://www.nabble.com/file/p17729256/Schermata.png") 


Thanks to all

---

### Post by franaria on 2008-06-09
Thanks to a GURU from the MONO forum I solved my problem. 
I had to install the libmono-dev 

This is the URL of the original post on MONO forum : 
[http://www.nabble.com/Re% 3A-MedSphere-GTK - Graph-widgets-to17696987.html]("http://www.nabble.com/Re% 3A-MedSphere-GTK - Graph-widgets-to17696987.html")

Thank you all anyway 
and thank you very much to **Brad Taylor** =D>

---

### Post by franaria on 2010-05-13
Hi all

 
In the past I have compiled the medsphere widgets on Ubuntu 8.04 but now with Ubuntu 10.04 I have problems.

 
When I run make I get the error below, you have some ideas to solve?

The source of the lib is here :
[http://medsphere.org/community/project/medsphere-widgets](http://medsphere.org/community/project/medsphere-widgets)
 
 
> ./IconLayout.cs(414,25): error CS0029: Cannot implicitly convert type `Cairo.Context' to `Cairo.Context' 
./IconLayout.cs(920,41): error CS1502: The best overloaded method match for `Gdk.CairoHelper.SetSourceColor(Cairo.Context, Gdk.Color)' has some invalid arguments 
/usr/lib/cli/gdk-sharp-2.0/gdk-sharp.dll (Location of the symbol related to previous error) 
./IconLayout.cs(920,41): error CS1503: Argument `#1' cannot convert `Cairo.Context' expression to type `Cairo.Context' 
./IconLayout.cs(920,41): (equally named types possibly from different assemblies in previous error) 
/usr/lib/mono/gac/Mono.Cairo/2.0.0.0__0738eb9f132ed756/Mono.Cairo.dll (Location of the symbol related to previous error) 
/usr/lib/mono/gac/Mono.Cairo/1.0.5000.0__0738eb9f132ed756/Mono.Cairo.dll (Location of the symbol related to previous error) 
Compilation failed: 3 error(s), 0 warnings 
make[1]: *** [Medsphere.Widgets.dll] Errore 1 
make[1]: uscita dalla directory «/home/franaria/.local/share/Trash/files/Medsphere.2.Widgets-0.2.1/src» 
make: *** [all-recursive] Errore 1 

 
Thank all

---


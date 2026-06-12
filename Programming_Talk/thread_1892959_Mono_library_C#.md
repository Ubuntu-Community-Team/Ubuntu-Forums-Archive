---
title: "Mono library C#"
date: 2011-12-09
forum: Programming Talk
---

### Post by Drenriza on 2011-12-09
Hi all.

Well i find the Mono packages a little confusing so i apologize if this is like some knowledge that all in the programming world know.

If i wan't ONLY to install the Mono packages to allow me to run C# code OR ASP.NET C# code. What packages would i need to install?

I am not intersted in all the packages like the development kit and such.
Only to compile and the runtime.

Thanks on advance to all.
Kind regards.

---

### Post by directhex on 2011-12-09
mono-xsp2 and mono-xsp4 contain the self-hosting ASP.NET app xsp2/xsp4, which will run a site from the current folder. If you want to integrate into Apache or some other web server, there are other things to install.

Beyond that, what you need depends on your code.

---

### Post by Drenriza on 2011-12-12
Hi Directhex.

Your good to make replys on my ASP.NET threads. I really appreciate it.
But can you elaborate on this
> Beyond that, what you need depends on your code.

What do you mean with, what i need depends on the code ?

Kind regards.

---

### Post by directhex on 2011-12-12
> **Drenriza said:**
> Hi Directhex.

Your good to make replys on my ASP.NET threads. I really appreciate it.
But can you elaborate on this


What do you mean with, what i need depends on the code ?

Kind regards.

I mean the system is designed to only pull in the bare minimum at any given moment - if you want to run ASP.NET "hello world", you're fine. If you want database access or ASP.NET MVC, you need to install more packages.

---

### Post by Drenriza on 2011-12-12
> **directhex said:**
> I mean the system is designed to only pull in the bare minimum at any given moment - if you want to run ASP.NET "hello world", you're fine. If you want database access or ASP.NET MVC, you need to install more packages.

What packages can i choose from? Is their a place that displays the packages available, and when you would need them?

Edit.
To throw it out their. Cant you install all the mono C# library,s for all the different types of code. Database, write to file, and what else their is.
Or else as i asked earlier. If their is a overview of packages versus function of each package, i would LOVE! to know. Thinking **_.NET 4.0_** sorry if i didn't state that earlier.

---

### Post by directhex on 2011-12-12
> **Drenriza said:**
> To throw it out their. Cant you install all the mono C# library,s for all the different types of code. Database, write to file, and what else their is.

Yes. The [mono-complete](apt:mono-complete) package installs everything.

> Thinking **_.NET 4.0_** sorry if i didn't state that earlier.

Then you need to use Oneiric or higher. Only Oneiric has .NET 4.0 support.

---

### Post by Drenriza on 2011-12-12
> Yes. The [[COLOR=#000000]mono-complete[/COLOR]]("apt:mono-complete") package installs everything.
Does that also include the mono-development kit? Since im not intersted in that. Only the stuff to run the runtime. Since i use visual studio for the coding.

---

### Post by directhex on 2011-12-12
> **Drenriza said:**
> Does that also include the mono-development kit? Since im not intersted in that. Only the stuff to run the runtime. Since i use visual studio for the coding.

You're using ASP.NET, so there's effectively no difference. You need the compiler installed, in order to compile aspx pages when they're visited.

---

### Post by Drenriza on 2011-12-13
> **directhex said:**
> You're using ASP.NET, so there's effectively no difference. You need the compiler installed, in order to compile aspx pages when they're visited.

Okey. So if i download Oneric and install mono-complete, do i then still need to install apache2 to make it run, or does mono-complete contain a web-server?

---

### Post by directhex on 2011-12-13
> **Drenriza said:**
> Okey. So if i download Oneric and install mono-complete, do i then still need to install apache2 to make it run, or does mono-complete contain a web-server?

mono-complete doesn't include any web server. You still need mono-xsp for the standalone server (really easy to use, useful for testing). Apache integration is done with other packages, but I'd recommend making sure your page works fine with XSP first before adding the complexity of apache configuration into the mix

---

### Post by Drenriza on 2011-12-13
> **directhex said:**
> mono-complete doesn't include any web server. You still need mono-xsp for the standalone server (really easy to use, useful for testing). Apache integration is done with other packages, but I'd recommend making sure your page works fine with XSP first before adding the complexity of apache configuration into the mix

Thanks for the info directhex.

---


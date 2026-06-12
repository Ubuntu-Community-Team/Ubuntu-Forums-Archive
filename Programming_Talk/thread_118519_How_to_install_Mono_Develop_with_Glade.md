---
title: "How to install Mono Develop with Glade ?"
date: 2006-01-17
forum: Programming Talk
---

### Post by Zonkle on 2006-01-17
Hi,

I downloaded the bin file for Mono library .. and now I need and IDE, so I found Mono Develop is best choice I think :? .. and I saw that there is Glade that adds Visual Interface to Mono Develop .... so can you please help me and tell me how can I install them ??

BTW, Mono Develop compile VB.Net right ?:?

Thanks all ;)

---

### Post by public_void on 2006-01-17
Its best to get the lastest release, but it means compiling from source, TBH its no biggy. The download page is [here]("http://www.monodevelop.com/Download"), also see the mono source page [here]("http://go-mono.com/sources"). They have all the .tar.gz's you need. There is a good step-by-step install for Ubuntu 64-bit here (It work fine on mine 32-bit). Just follow the steps and it should go well. I didn't use the wget command as in the step-by-step, instead I download all I needed to one directory and worked from there. You should note that there is no visual form designer like in Visual Studio, you have to use Glade to create the GUI and write code to use the glade file as the GUI, it isn't hard, but IMO takes a bit of getting use to. And yes you can create VB projects.

Odd note: The step-by-step seem to apear wrong in my browser (IE, typical) with the beginning of it half-way down the page.

---


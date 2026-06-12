---
title: "Moonlight as Linux substitute for MS Silverlight"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by Curtis6767 on 2012-01-30
In hopes of viewing freestockcharts.com, which is a Silverlight site, I found Moonlight and then did a search within the Ubuntu software center and found and then downloaded Mono WFC libraries (for CLI 2.0)  but I still can't view the page.

Any ideas on what I might have to do?

Maybe Moonlight won't work on that site or maybe Moonlight doesn't work at all.

---

### Post by lykwydchykyn on 2012-01-30
Moonlight only supports silverlight up to a certain point (version 2 or 3 I think), and even then there are things that don't work.

As far as I have been able to tell by reading developer blogs and published emails, moonlight development is on life support since the Novell split-up.  The team that was working on it split off into a company called Xamarin, and they are no longer interested in pushing Moonlight forward.

So basically, at this point the future of Silverlight on Linux is pretty grim.

---

### Post by rgreener25 on 2012-01-30
You could use [chart.ly]("chart.ly") instead

---

### Post by Curtis6767 on 2012-01-30
I did a search of sites that use Silverlight and it seemed as though some of those sites loaded their Silverlight content into FF9. Maybe it was Flash. Not sure.

I went to Moonlight and tried to down load their Linux plug in and at the end of the download was informed that Moonlight was not supported by FF9. 

Chart.ly, not sure what you mean by that. Just charts there but not streaming real-time charts that FreeStockCharts supplies. Did I miss something?

Thanks.

---

### Post by Frogs Hair on 2012-01-30
I read that the reason Moonlight does not work with certain content is that it lacks DRM support and it is not due to it being out of date . The license its self prohibits DRM support which is included with Silverlight .

---

### Post by QIII on 2012-01-30
Who was that very large software company that threw in with the DRM movement and benefitted by getting pretty much sole rights to include it in their OS?   The name escapes me now.

Ximarin also got Mono as part of the Novell ballast cast off, so if you were dreaming of .NET development for Linux, be prepared with a bottle of oxygen to try to keep the patient alive.

---

### Post by directhex on 2012-01-31
Moonlight has no active upstream developers. Novell were funding it, and there were 0 community-based developers. Xamarin have no interest in continuing its development, so it's a dead project.

[quote=QIII]Ximarin also got Mono as part of the Novell ballast cast off, so if you were dreaming of .NET development for Linux, be prepared with a bottle of oxygen to try to keep the patient alive.[/quote]

It might not fit your little fantasy, but Xamarin has been hiring. Mono is healthier now under Xamarin than it was under Novell.

---

### Post by QIII on 2012-01-31
My "little fantasy" is based on the fact that de Icaza has about 50 employees he gathered mostly from the original 30 or so people who worked on Mono and their self-sustaining revenue, even with the deal they made with SUSE, is tenuous and they'd better keep Novell's old clientelle happy.

"Is hiring" may be a bit of a stretch.  "Hired more" may be more accurate.

Same customers, same product (add Ice Cream Sandwich), same crew.  Things may be exciting right now.  But for a start up, the excitement is normal.  Are things better than ever?  Depends on how you define that.

If you are an Android developer, maybe.  But that would be a bit of an iffy hook on which to hang too heavy a hat if it were your only one.

Without a large corporate financial buffer,  Miguel could be in a soup line tomorrow with a lot of other excited start up entrpreneurs.

---


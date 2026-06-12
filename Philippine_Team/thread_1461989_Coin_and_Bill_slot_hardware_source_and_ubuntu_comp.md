---
title: "Coin and Bill slot hardware source and ubuntu compatibility, any ideas?"
date: 2010-04-25
forum: Philippine Team
---

### Post by confulity on 2010-04-25
Mga sirs,

Magandang ubuntu po sa inyong lahat, meron na po ba ditong mga nakagawa/nakagamit na ng coin and bill slot na hardware yung pwedeng i interface sa isang program sa pc? naghahanap ako ng source and willing tumulong mag develop (with enough talent fee) , for ubuntu marketing po sana.. sana may nakaka alam po.. salamat..

:popcorn:

---

### Post by Script Warlock on 2010-04-25
hmmm interesting...

---

### Post by confulity on 2010-04-26
Mga sirs,

meron na po bang nakapag develop sa inyo ng software na ginagamitan ng coin slot or bill acceptor slot. parang ganto po..

[http://www.cheapkiosks.com/Bill_Acceptor.aspx](http://www.cheapkiosks.com/Bill_Acceptor.aspx)

---

### Post by badrra on 2010-04-27
Serial programming. I am trying to remember kasi nagawa ko na to pero ilang taon na heheheh. 

Let see, alam ko yang bill acceptor meron syang mga signals na binibigay pag activated na sya. Like pag merong pumasok na bill, accepted ba, binalik ba or rejected, etc. And also merong state sya, naka hold ba na pwedeng ibalik o pwedeng tangapin, or natangap na na nasa bin na sya, and also kung magkano nilagay. 

Merong mga switches yan sa likod like kung 20PHP, 100PHP, 500 PHP nilagay merong correspionding code sya. 

When activating the device, dedicated yung isang serial port for communication lang. Either comport1 or comport2 (obvuously heheheh). Thats as far as I can remember. 

Hope it helps. good luck,

Overall madali lang sya.

---

### Post by badrra on 2010-04-27
Alam ko to kasi I was able to develop a prototype ng isang top-up application for globe, smart and sun prepaid. 

But that was years ago.

---

### Post by confulity on 2010-04-28
@badrra

nice nice.. salamat salamat.. pwde ko bang makuha ang contact number mo po sir?

- Meron ka po bang source na pwedeng pagkunan nito sa pinas?..
- If meron po magkano yung sa bill acceptor? yung sa coin slot naman po?
- Anong O.S. po yung pinag gawan nyo ng prototype?
- Aattend po ba kayo ng release party sa may 7?

meron na po akong nakitang mga source e, kaso chine and not sure kung maddetect sa linux/ubuntu..

ito po sila

[http://www.weavefuture.com/](http://www.weavefuture.com/)

[http://www.highway.net.au/news/146.html](http://www.highway.net.au/news/146.html)

[http://www.uniarcade.com/coinop_system/usb_coin_box.htm](http://www.uniarcade.com/coinop_system/usb_coin_box.htm)

[http://www.cheapkiosks.com/Bill_Acceptor.aspx](http://www.cheapkiosks.com/Bill_Acceptor.aspx)

salamat po sir.. rock and roll..

:guitar:

---

### Post by badrra on 2010-04-28
> **confulity said:**
> @badrra

nice nice.. salamat salamat.. pwde ko bang makuha ang contact number mo po sir?

- Meron ka po bang source na pwedeng pagkunan nito sa pinas?..
- If meron po magkano yung sa bill acceptor? yung sa coin slot naman po?
- Anong O.S. po yung pinag gawan nyo ng prototype?
- Aattend po ba kayo ng release party sa may 7?

meron na po akong nakitang mga source e, kaso chine and not sure kung maddetect sa linux/ubuntu..

ito po sila

[http://www.weavefuture.com/](http://www.weavefuture.com/)

[http://www.highway.net.au/news/146.html](http://www.highway.net.au/news/146.html)

[http://www.uniarcade.com/coinop_system/usb_coin_box.htm](http://www.uniarcade.com/coinop_system/usb_coin_box.htm)

[http://www.cheapkiosks.com/Bill_Acceptor.aspx](http://www.cheapkiosks.com/Bill_Acceptor.aspx)

salamat po sir.. rock and roll..

:guitar:

Di po ako sigurado dyan sa mga link or sa producto nila. Ginawa ko ito sa windows dati pero di ko lang matandaan ang drivers na ininstall ko. Alam ko wala na pero di ako sigurado. 

Ginami ko Visual basic at alam ko plug and play na ito. Di rin ako sigurado kung gagana sa linux. Dapat i consult mo yung manufacturer for this. 

Ginawa ko ito para sa isang kompanya, di na ko mag elaborate kung anong project nila kasi bawal. Pero ang alam ko galing singapore yung bill acceptor nila. If I remember it ight, "Matrix" ang tawag sa kanya. Di lang ako sigurado kung merong rep ito.

---


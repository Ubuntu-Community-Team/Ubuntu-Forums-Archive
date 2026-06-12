---
title: "Substitute for Voip Discount calling software"
date: 2014-12-13
forum: New to Ubuntu
---

### Post by avishek2 on 2014-12-13
Hi,

I am living in Germany and I have these vouchers from **Ukash** which I was using with **Voip Discount**.

Now that I have just switched to ubuntu I have no idea which software to use for making calls from computer to phones, where I can keep using my Ukash vouchers!

Please advice guys!

Thanks!

---

### Post by DuckHook on 2014-12-14
Re: Ukash

I had never heard of this one until you posted. Here in NA, Paypal tends to be more widespread, but they are somewhat similar concept. I don't know the details, but it seems that the vendor must accept payment in this form, in which case, it can be handled on any web-based browser. Therefore, all you need to do is find a VOIP vendor that makes an app for Linux.

Re: VOIP App

I don't use Skype. It's a Microsoft product that is clearly being positioned to drop Linux support soon. There have been many reports on different sites and even on these forums that the Linux version is increasingly buggy, obsolete, missing features and very much an afterthought at this point.

I've recently gone to Viber. You have to download the deb file from their site as it is not in the Software Centre. I do not believe that it takes Ukash.

Google also has a VOIP web applet, but it only works in the US for now. It looks very slick, but is not useful for you in Germany until Google extends support into your country.

Others may be able to point you to other VOIP solutions.

As for using up your Ukash vouchers, you may just have to use them on Christmas presents and not VOIP vendors.:)

---

### Post by avishek2 on 2014-12-15
Thanks for the tip, but does Viber allow calls from computer to mobile phone? 

[http://www.viber.com/products/linux](http://www.viber.com/products/linux) seems unclear in this respect.

---

### Post by DuckHook on 2014-12-15
> **avishek2 said:**
> Thanks for the tip, but does Viber allow calls from computer to mobile phone?
Yes it does. You can dial out to any "landline". It costs a small charge that varies from country to country.

---

### Post by sandyd on 2014-12-15
> **avishek2 said:**
> Hi,

I am living in Germany and I have these vouchers from **Ukash** which I was using with **Voip Discount**.

Now that I have just switched to ubuntu I have no idea which software to use for making calls from computer to phones, where I can keep using my Ukash vouchers!

Please advice guys!

Thanks!
You can keep on using VOIPDiscount. It happens to have a SIP setup that you can use with any softphone.
Try SFLPhone - ive used it with PBXes, and VOIP providers like voip.ms/anveo/etc without issues.

See [http://www.voipdiscount.com/sip](http://www.voipdiscount.com/sip) for sip details. Ignore the top part, and go straight down to the Software Configuration

---

### Post by DuckHook on 2014-12-15
> **avishek2 said:**
> Thanks for the tip, but does Viber allow calls from computer to mobile phone? 

[http://www.viber.com/products/linux](http://www.viber.com/products/linux) seems unclear in this respect.I may have misunderstood your question...

To follow up on my first answer:

If you are speaking of a Viber-to-Viber call, then yes, it allows for free calling from your computer to your phone, provided you are calling your phone's Viber app and not your carrier's phone number. Even so, it's not really "free", since you are using up your phone's data plan, but you get the gist of what I mean.

I note that *sandyd* has given you further info that may render Viber academic. I would recommend any mod's advice over mine as they have the greater knowledge and experience and are well worth listening to.

---

### Post by spiffymoo on 2014-12-17
use google hangouts

---

### Post by carl4926 on 2014-12-17
> **sandyd said:**
> You can keep on using VOIPDiscount. It happens to have a SIP setup that you can use with any softphone.
Try SFLPhone - ive used it with PBXes, and VOIP providers like voip.me/anveo/etc without issues.

See [http://www.voipdiscount.com/sip](http://www.voipdiscount.com/sip) for sip details. Ignore the top part, and go straight down to the Software Configuration

Good advice

Most voip providers will have a SIP setup and the same has proved true for me
Though I was using Linphone for a long time, now,since the voip company issued an android app, I just use my Cell phone

---

### Post by avishek2 on 2014-12-17
Hey sandyd,

I installed SFLPhone and the information required on the account settings page do not correspond with the software configuration info provided here: [http://www.voipdiscount.com/sip](http://www.voipdiscount.com/sip).

For instance SFLPhone wants a **Hostname** where I have used the **Registrar** (sip.voipdiscount.com).

I have an Internal Server Error 500 for the voip discount account.

Please advice!

---

### Post by carl4926 on 2014-12-17
> **avishek2 said:**
> Hey sandyd,

I installed SFLPhone and the information required on the account settings page do not correspond with the software configuration info provided here: [http://www.voipdiscount.com/sip](http://www.voipdiscount.com/sip).

For instance SFLPhone wants a **Hostname** where I have used the **Registrar** (sip.voipdiscount.com).

I have an Internal Server Error 500 for the voip discount account.

Please advice!

Actually that looks like the same service I use but trading under one of it's many different names.
I'm not sure of the settings of SLFPhone. But some settings such as you mention, may not be that important

---

### Post by sandyd on 2014-12-18
> **avishek2 said:**
> Hey sandyd,

I installed SFLPhone and the information required on the account settings page do not correspond with the software configuration info provided here: [http://www.voipdiscount.com/sip](http://www.voipdiscount.com/sip).

For instance SFLPhone wants a **Hostname** where I have used the **Registrar** (sip.voipdiscount.com).

I have an Internal Server Error 500 for the voip discount account.

Please advice!
Sorry about taking a bit long to respond - holidays and such are taking a bit more out of my schedule than normal.

Have you enabled SIP in your voipdiscount account? - See [https://www.voipdiscount.com/customerservice/article/654](https://www.voipdiscount.com/customerservice/article/654)

---


---
title: "firefox 3.0.3 upgrade"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by jordilin on 2008-09-28
I just upgraded to firefox 3.0.3 from repos, and now every time I log in to windows live hotmail, windows live does not recognized firefox as a supported browser and tells you to install firefox (between other choices :)). I didn't have any problem with firefox 3.0.2. Has anything changed at all? The thing is I cannot reply emails by using 3.0.3 and I could with 3.0.2. 
I use ubuntu hardy 8.04 64bit. If anyone knows how to downgrade to 3.0.2, would be much appreciated.

---

### Post by Dougie187 on 2008-09-28
I don't think it's telling you to install firefox. It tells you to update to windows live hotmail. If you read all of it there is a link in the bottom section that you can click to bypass the issue.

I may be wrong, but this is what happens to me. If I am wrong, take a picture and post it please. Thanks.

---

### Post by SuperSonic4 on 2008-09-28
I just think is M$ being slow to recognise a product that it did not make.

Just click the "continue..." link and all will be good

---

### Post by terry_gardener on 2008-09-28
i have just tested this and supersonic4 is right click the continue... link where is says i dont want to upgrade.

---

### Post by jordilin on 2008-09-28
Well, yes I click the continue button and then I can read the email. The problem is when I have to reply emails. When I'm going to reply, I cannot write in the body of the email. I should have specified a bit more I guess :)

---

### Post by terry_gardener on 2008-09-28
i have just tried to reply to an email and it worked for me. 

if you want to install firefox 2 again. just open synaptic and search firefox and install it, then you can use firefox 2 for email with hotmail.

---

### Post by terry_gardener on 2008-09-28
do you have any security software running in firefox for example noscripts, adblock or anything link that if so try disabling it and retry.

---

### Post by jordilin on 2008-09-28
> **terry_gardener said:**
> do you have any security software running in firefox for example noscripts, adblock or anything link that if so try disabling it and retry.

I had the adblock plus add-on, but I have disabled it and it continues with the same problem. I have javascript enabled as well in preferences. The toolbar in the email body is greyed-out, so I guess this is javascript being blocked. 
I have an additional, clean profile in firefox, and I still have the same nasty problem. In version 3.0.2, I had the same security profile setup with the adblock plus add-on and I didn't have any problem at all.

---

### Post by terry_gardener on 2008-09-29
sorry which toolbar are you refering the one with attach files etc on. 

can you supply a screenprint off the fault. 

because this works on mine and another pc that i tested it with both have been upgraded to firefox 3.03

---

### Post by JARGXero on 2008-09-29
I got the same issue, except for the reply thing.

With this new upgrade the FULL VERSION of Windows Live Hotmail doesn't run. All I get is the classic version and there are some limitations, and I just don't like it at all.

I barely use Hotmail, but I need it for some important contacts.

Can anything be done to solve this?

---

### Post by jordilin on 2008-09-29
> **terry_gardener said:**
> sorry which toolbar are you refering the one with attach files etc on. 

can you supply a screenprint off the fault. 

because this works on mine and another pc that i tested it with both have been upgraded to firefox 3.03

Here I leave attached a screenshot of the problem.
The toolbar is greyed out and I cannot write anything (not editable) in the email body

---

### Post by terry_gardener on 2008-09-29
sorry i dont use hotmail very much at all. 

i didn't realise that there had a full version and classic version i was testing the classic version which seems to work. 

i have also tried tricking MS site by using the user agent switcher addon in firefox, gives you the option to switch to full version but it doesn't load.

i cleared the cache and privacy data still didn't load.

firefox 3.0.3 works in windows but the new google chrone doesn't with the full version of hotmail. 

it would seem that MS are limiting this service to certain browsers and OS's.

I am going to try it with ubuntu intrepid but not expecting much. i will let you know the results.

---

### Post by wavingpines on 2008-09-29
I got the same warning on entry to hotmail but having taken the 'continue to Windows Live Hotmail' option, everything appears to work OK.  I guess we just have to wait for Uncle Bill & Co. to recognise this new version.

---

### Post by terry_gardener on 2008-09-29
i have tried ubuntu intrepid and the same thing happens. 

does look like we are going to have to wait for MS to sort this out.

---

### Post by jordilin on 2008-09-29
> **terry_gardener said:**
> i have tried ubuntu intrepid and the same thing happens. 

does look like we are going to have to wait for MS to sort this out.

Yeah, apparently MS does not recognize firefox 3.0.3. We will have to await...

---

### Post by GregMcn on 2008-10-01
Same problem here also.I tired Opera and it worked ok with that browser.will try a few other browsers as well and see.Guess its the only solution for now.

---

### Post by rbnwmk on 2008-10-06
Same here using firefox upgraded through Ubuntu's repositories.

OS: Ubuntu 8.04 32bit

But then, I tried:

1. Downloaded Firefox directly from Mozilla website, then extracted into "/home/user/" directory.

2. Ran "./firefox" from there to access Hotmail, was able go into inbox straight. No incompatibility warning appeared.

3. Ran again default Ubuntu installed firefox to access Hotmail, same warning appeared.

4. Repeat step 2, no warning.

5. Repeat step 2 again, no warning.

6. Repeat step 3, Arrggh!! it's back!!

So, it seems Ubuntu did something in Firefox that M$ don't like... discriminated by M$?? :-k

---

### Post by jordilin on 2008-10-07
> **rbnwmk said:**
> Same here using firefox upgraded through Ubuntu's repositories.

OS: Ubuntu 8.04 32bit

But then, I tried:

1. Downloaded Firefox directly from Mozilla website, then extracted into "/home/user/" directory.

2. Ran "./firefox" from there to access Hotmail, was able go into inbox straight. No incompatibility warning appeared.

3. Ran again default Ubuntu installed firefox to access Hotmail, same warning appeared.

4. Repeat step 2, no warning.

5. Repeat step 2 again, no warning.

6. Repeat step 3, Arrggh!! it's back!!

So, it seems Ubuntu did something in Firefox that M$ don't like... discriminated by M$?? :-k
Yes, apparently firefox 3.03 from Ubuntu is screwed. I repeated the same and it works fine from mozilla offical website

---

### Post by jordilin on 2008-10-07
I reported a bug in launchpad Bug #279802 
Having the same firefox version in Ubuntu should not make any difference by using the one from mozilla and should be addressed asap.

---

### Post by john_navarro on 2008-10-09
The User Agent Workaround described here works for me - might be a good solution for some of you:

[http://www.freesoftwaremagazine.com/columns/hotmail_doesnt_work_with_firefox_2](http://www.freesoftwaremagazine.com/columns/hotmail_doesnt_work_with_firefox_2)

---

### Post by rbnwmk on 2008-10-10
Thank You~! john_navarro

Thanks for the advise. I couldn't really understand things described at your link, so with your useragent hint, I googled further and found an easier solution that worked for me, hope this help the rest too.

1. Type about:config at firefox URL field and press enter.

2. Click on "I'll be careful, I promise!" button. (Sure, thanks.. :tongue: )

3. Then at the top filter field, type useragent to make "general.useragent.vendor" name in sight.

4. Double click "general.useragent.vendor" to change the value from Ubuntu to Firefox.

5. Done!

---

### Post by jordilin on 2008-10-10
> **rbnwmk said:**
> Thank You~! john_navarro

Thanks for the advise. I couldn't really understand things described at your link, so with your useragent hint, I googled further and found an easier solution that worked for me, hope this help the rest too.

1. Type about:config at firefox URL field and press enter.

2. Click on "I'll be careful, I promise!" button. (Sure, thanks.. :tongue: )

3. Then at the top filter field, type useragent to make "general.useragent.vendor" name in sight.

4. Double click "general.useragent.vendor" to change the value from Ubuntu to Firefox.

5. Done!

I just tried myself and it works as well, really weird.

---

### Post by styrofoam cup on 2008-10-25
It works for me also, but the value keeps changing back to the default of Ubuntu. Is there a way to make the change permanent?  

Thanks


EDIT - I found why it kept resetting back to Ubuntu for the useragent in about:config. It was caused by having the useragent plugin installed. After removing it and manually changing the useragent from Ubuntu to Firefox/3.0.3 hotmail is working right.

---

### Post by tuskenraider on 2008-10-25
gmail + thunderbird + pop3 access = WIN! :lolflag:

---

### Post by Cebonet on 2008-10-25
I know this isn't the solution but, I will prefer you to use Thunderbird and then install the Webmail(add-ons). It's works great!:) Sorry this is "off" the solution.

---

### Post by mdsmedia on 2008-10-25
> **tuskenraider said:**
> gmail + thunderbird + pop3 access = WIN! :lolflag:
+1, although that's not a solution to the hotmail problem.

I still have a hotmail address (Live ID for some things that require it for login), but haven't used Hotmail for email for a LONG time.

I host my domain's email in Google Apps (gmail) and imap to Thunderbird. gmail's Pop functionality isn't as simple with hosted addresses. Imap works great though. Is there a Pop feature in Hotmail?

---


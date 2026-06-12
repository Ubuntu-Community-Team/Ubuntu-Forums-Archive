---
title: "Slow internet but I want to test"
date: 2018-09-16
forum: New to Ubuntu
---

### Post by dave6 on 2018-09-16
Hi guys.

I use to have 18mb internet, up until April this year ( or there abouts ) but it has gone down hill ignoring the internet 
I want to set up some type of test, as maybe the "System Monitor / Network History" is mis-reporting it. ? see screen shot.  Should add at this point, that the ISP tell me I am getting 17.9mb yet when I run the test on the site they recommend for testing you can see the result.

I have a second computer here in the house if I was to do a clean install unto it of some 32bit software and then some how link the 2 computers together this one and that one, via the ADSL router that I am using and send a large file 5gb across the system so as I can see the speed using patch cables not wifi how would I go about doing that.

Or, can some one recommend a site that I could download a large file from and keep an eye on a watch to see the length of time required.. I do not want to do a speed test from the likes of speedtest dot com  

Any ideas or suggestions would be great, it may also help others that have slow internet speeds to confirm where a fault lies at.

Thanks 
Dave

---

### Post by Autodave on 2018-09-16
There are MANY sites that you can test your speed on.  Just Google "Internet speed test" and try a couple of them.  That should give you a good idea of your speed.  Remember: to get an accurate result, make sure that ONLY your PC is using the internet when you run the test.

---

### Post by dave6 on 2018-09-16
thanks autodave for your reply: I may not have made myself clear enough,  

I want to test the computer, patch cable to router to a second wired computer which I have here in the house.  reason being is to rule OUT this part of the system
Consider this, the ISP or the MANY sites tell you, that your system can download at 15MB/s you go to download a 300MB file, with my counting it should take 20 seconds. 300 divided by 15 = 20...............BUT ! it takes 10 minutes? where is the bottle neck at, where is your 15MB/s at that the MANY "Internet speed test" tell you... It is not the internet speed I am looking for at this point in time.

I have been told by a retired BT engineer and a retired radar technician, "who wrote a book on radar signal propagation" the test equipment used by BT and other test sites send only one ping to measure speed while the computer sends 4 pings or data packages 

Like I said, if you had looked at the screen shot I provided: the ISP tell me I am getting 17.9mb yet when I run the test on the site they recommend. This time it showed 11.3, while the Mate "System Monitor / Network History" showed 100 kb/s 

If some one could tell me how to run a test from computer to computer, it would be very helpful, and maybe even for others who are being fobbed off by their ISP about slow speeds.

Dave

---

### Post by The Cog on 2018-09-16
There is a program called iperf which can measure network performance. The command "apt show iperf" will give you a description.

But you would be wasting your time. You local network will not be the problem.

An internet link speed of 15 Mb/S (15 megabits per second) will be capable of carrying at best 1.875 MB/S (megabytes/Sec). At that rate, a 300 megabyte file would take 160 seconds - just over 2.5 minutes. And if you are using a dumb file manager that shows file sizes in mebibytes, that's really 315 megabytes which would take 168 seconds.

For 315 Mib in 10 minutes, that equates to 4.2 Mbit/Sec, but that's just payload. The TCP headers will add a few percent to that. I estimate you are getting 1/3 to 1/4 of the ISP's stated speed.

So you are still getting quite a bit less than 15Mb/S on your file transfer, but it's not as bad as you think. Bear in mind that your transfer will be contending for ISP bandwidth with other users so you may well not get 15 M throughput except in the small hours of the morning.

---

### Post by Geoffrey_Arndt on 2018-09-16
Just have your internet  provider tech look at your system and make upgrade recommendations.   Perhaps upgrading relatively slow ADSL to ADSL+ or other hardware.  

As the "Cog" writes, comparing intranet speeds to internet speeds is an invalid method to check speed.   The ISP may have made additional changes that precipitated your net speed reductions.   Do you have any competition in your area for internet services?

---


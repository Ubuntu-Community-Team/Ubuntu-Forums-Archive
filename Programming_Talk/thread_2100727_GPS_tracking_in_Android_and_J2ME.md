---
title: "GPS tracking in Android and J2ME"
date: 2013-01-02
forum: Programming Talk
---

### Post by 3v3rgr33n on 2013-01-02
Hi

I want to build a system whereby people get to track their pets or livestock using their cellphones.

I want to make this for android smartphones and use J2ME for the older phones. Before I start programming however
1. I just wanted to find out is this possible (GPS trackin that is) ?
2. Surely there needs to be a device on the animals to emit the GPS signal, is there an inexpensive way of making such devices?

Regards

---

### Post by chadk5utc on 2013-01-02
Hello there are currently systems available online to monitor/find lost "pets" they use gps and require subscriptions as they do in fact use satellite data then send the data to some ground based station which translates the data and places it on a website where users can login and view their devices. A quick google search
[http://www.pettracker.com/?utm_source=Google&utm_medium=banner&utm_campaign=Winter2013](http://www.pettracker.com/?utm_source=Google&utm_medium=banner&utm_campaign=Winter2013)
[https://www.google.com/search?q=gpd+dog+tracking&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a#hl=en&client=firefox-a&hs=jzp&tbo=d&rls=org.mozilla:en-US%3Aofficial&sclient=psy-ab&q=gps+dog+tracking&oq=gps+dog+tracking&gs_l=serp.3..0i7l3j0.181204.181353.0.181527.2.2.0.0.0.1.178.298.0j2.2.0.les%3B..0.0...1c.gzudUkkjjSA&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&bvm=bv.1355534169,d.eWU&fp=eeaed9fac54bfaee&bpcl=40096503&biw=1024&bih=463](https://www.google.com/search?q=gpd+dog+tracking&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a#hl=en&client=firefox-a&hs=jzp&tbo=d&rls=org.mozilla:en-US%3Aofficial&sclient=psy-ab&q=gps+dog+tracking&oq=gps+dog+tracking&gs_l=serp.3..0i7l3j0.181204.181353.0.181527.2.2.0.0.0.1.178.298.0j2.2.0.les%3B..0.0...1c.gzudUkkjjSA&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&bvm=bv.1355534169,d.eWU&fp=eeaed9fac54bfaee&bpcl=40096503&biw=1024&bih=463)

Having stated all this there are a growing number of gps devices available and their size continues to shrink last one I priced was about $200 per unit plus monthly service for satellite access but that was some time ago. In addition there are radio frequency and licensing considerations.

---

### Post by 3v3rgr33n on 2013-01-02
I see. I wanted to build my own thing just for fun.

> ...require subscriptions as they do in fact use satellite data then send the  data to some ground based station which translates the data..
I'm not necessarily looking for GPS tracking, just the tracking part that interests me!

Isn't there a way of building a system without the subscriptions and all that?
I don't want to do something that will burden people with expensive data costs.

---

### Post by Cheesehead on 2013-01-02
> **3v3rgr33n said:**
> 1. I just wanted to find out is this possible (GPS trackin that is) ?
2. Surely there needs to be a device on the animals to emit the GPS signal, is there an inexpensive way of making such devices?
Certainly it's possible...but it may not be worthwhile. Location data is different from GPS data is different from other types of data.

Each type of data has a different cost, and a different use. Your use cases need to define the markets you want to create for.

Examples of different data:
- Location data: Fluffy's tracking collar is somewhere within range of my home wi-fi.
- GPS data: Fluffy's tracking collar is at 43.23456N, -88.23456W +/-10m
- Event data: Somebody just peed on the Living Room rug sensor. I hope it was Fluffy.
- Camera data: A cat is standing on the rug in the Living Room. 80% match to Fluffy's stored image.
- RFID data: Fluffy's RFID chip just passed the kitchen door reader.

Each type of data requires different equipment, different setup, and has different costs. What level of detail is your customer willing to pay for?

Example:
Livestock owners care about inventory control, not GPS location. Several that I know prefer RFID data. They don't care where each cow is grazing in the pasture. They do care that the whole herd went to the pasture in the morning, and the whole herd returned.

Dairy herds also use RFID extensively to identify each cow to the production management system. The system tracks each cow's milk output, and the reader IDs each cow as she enters the milking stall.

Example:
Some pet owners will care deeply about what room their pet is in...but they are almost certain to want camera images more than GPS readouts. It might be easier to use visual ID and motion-sensing to track the pet using existing cameras instead of a second technology. Also, GPS is unreliable indoors - the signal may not penetrate many walls or roofs.

Example: Some pet owners want to track pets merely in order to recover a lost pet. That's a variation on inventory control, and already filled by embedded RFID chips available at any veterinarian office.

Do you have a more specific usage example?

---

### Post by 3v3rgr33n on 2013-01-03
> ...They don't care where each cow is grazing in the pasture. They do care  that the whole herd went to the pasture in the morning, and the whole  herd returned...

I'm sorta looking for the case when not all the herd has returned, I'm sure people might need a quick way to know where to look for first (assuming that it can wander off freely).

---

### Post by Cheesehead on 2013-01-04
Then you care about transmitter power and frequency.

Those determine how many receivers you need (one on a satellite, or several hundred scattered about). Transmitter power also determines how often somebody changes all those transmitter batteries. 

Some animals may need to be restrained to safely change batteries. Infrastructure and batteries are expensive...but an employee kicked in the head while changing batteries can be even more expensive.

If you can figure out a way to reduce the infrastructure or reduce the employee injury risk, you might have a successful product.

---

### Post by chadk5utc on 2013-01-04
> **Cheesehead said:**
> Then you care about transmitter power and frequency.

Those determine how many receivers you need (one on a satellite, or several hundred scattered about). Transmitter power also determines how often somebody changes all those transmitter batteries. 

Some animals may need to be restrained to safely change batteries. Infrastructure and batteries are expensive...but an employee kicked in the head while changing batteries can be even more expensive.

If you can figure out a way to reduce the infrastructure or reduce the employee injury risk, you might have a successful product.

Great idea I know this can be done and has been done. Here are some links that may give you ideas
[http://playground.arduino.cc/Tutorials/GPS](http://playground.arduino.cc/Tutorials/GPS)
[http://arduino.cc/en/Main/Products](http://arduino.cc/en/Main/Products)
Several years ago I did a project for my daughters class and launched a high altitude balloon with mini flight computer radio transmitter and gps to over 70k feet flight time of @2hrs and traveled over 100 miles which we later recovered.

---

### Post by 3v3rgr33n on 2013-01-05
I was really hoping for a really easy solution.

Making an inexpensive gps location transmitter that people can hook to the 'trackee' and use their phones to track perhaps.

---


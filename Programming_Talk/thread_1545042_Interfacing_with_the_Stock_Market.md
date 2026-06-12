---
title: "Interfacing with the Stock Market"
date: 2010-08-03
forum: Programming Talk
---

### Post by druca on 2010-08-03
Hello,

Excuse me if this is quite the naive question, but I wanted to make a stock bot, that would buy/sell shares based on set parameters. 

Does anyone know of any resources that could help me?

Preferably Direct Market Access but it seems I have to be a licensed broker to do so, is this true?

Everyone and their mother seems to have an API for various markets, I wanted to cut the middle man out of the way and do it myself. 

Is there any free ones? 

Thank you,
Drew

---

### Post by oldfred on 2010-08-03
I do not think there is anything like what you want. Seems very risky as if you logic is off you can get in deep trouble quickly.

Finance/Stocks
In synaptic
Qtstalker is a user friendly Technical Analysis package for GNU/Linux.  It
is similar to commercial software such as Metastock, Supercharts and
Tradestation.
[http://jstock.sourceforge.net/](http://jstock.sourceforge.net/)
[http://www.chartsy.org/](http://www.chartsy.org/)

---

### Post by druca on 2010-08-03
Thank you. Any other suggestions anyone?

---

### Post by CptPicard on 2010-08-03
Actual *direct* market access is a tough one, you really need to be a broker that meets very strict requirements to actually operate straight on the market itself. This is because a broker has much more responsibilities on the market itself as a direct counterparty to other operatives on the said market.

But you certainly do not need that. It is quite sufficient to have an API to broker. Personally I've always preferred having signals from algorithms, but being the guy who actually pushes the buttons in the end.

---

### Post by druca on 2010-08-04
Thank you for your answer I appreciate that. I'll mark as solved.

If anyone is interested, here are a few things I found. 

[www.forex.com](www.forex.com) offers an API, however FOREX is a different exchange entirely. Trading currencies etc. 

This is offered by the NYSE Eurnonext 
[http://www.nyse.com/technologies/tradingsolutions/1222942098129.html](http://www.nyse.com/technologies/tradingsolutions/1222942098129.html)

The Financial Information eXchange (FIX) Protocol is a messaging standard developed specifically for the real-time electronic exchange of securities transactions. FIX is a public-domain specification owned and maintained by FIX Protocol, Ltd.
source:
[http://www.fixprotocol.org/](http://www.fixprotocol.org/)

You have to buy this one.
[http://www.visionfinancialmarkets.com/securities/services/activetrading/](http://www.visionfinancialmarkets.com/securities/services/activetrading/)

Anyway the list can go on...

I endorse none of these whatsoever just something to add to a google search in case anyone else is interested.

Thanks,
Drew

---

### Post by druca on 2010-08-04
Its called Black Box Trading in case anyone is wondering.

---

### Post by CptPicard on 2010-08-04
Generally fully algorithmic trading requires rather minimal latency too... it's hard to achieve from somewhere else except physically close to a brokerage's systems.

I spent a couple of years trading almost full time, personally I find that combination of man and machine is the optimal one in your typical intraday trading where you may hold a position for from 15 minutes to most of a day. The human being is capable of making judgement calls based on all kinds of contextual information, while the machine can find, for example, good trading setups for you to consider... in general it started to seem like that my own seat of pants feeling was, with sufficient experience, superior to any single automated strategy.

Besides, 100% automated quant trading is very much a big boys' game; you should leave it to the big boys. :)

---


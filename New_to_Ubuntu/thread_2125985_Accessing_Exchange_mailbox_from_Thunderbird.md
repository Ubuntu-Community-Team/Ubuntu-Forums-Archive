---
title: "Accessing Exchange mailbox from Thunderbird?"
date: 2013-03-15
forum: New to Ubuntu
---

### Post by wi11iamr on 2013-03-15
Hi there,

I'm an absolute noob to Ubuntu, but I've been plodding along nicely the past 3 weeks. I've setup my IMAP mail account without any hassles on Thunderbird 17.04, but I'm quite clueless about how to connect to my company's Exchange server.

Is there an "easy" way to do so? I've read about using a product called Evolution, and/or ensuring that the Exchange server has IMPA enabled. I'm hoping there is a somewhat more generic client-side solution I can find on my own workstation?

Regards
William R.

---

### Post by DuckHook on 2013-03-15
Welcome to the forums (and to Ubuntu). Hope you are enjoying the experience.

Evolution is an alternate mail app and would replace T-Bird if you decide to use it. Whether you can use T-Bird depends entirely on how the Exchange server is set up. If it is set up to support IMAP and/or POP3, then T-Bird can be configured to connect (these are the only 2 protocols that T-Bird supports). However, if the Exchange server is set up to only use its native protocol, then you will have to use Evolution. Apparently, an add-on called ExQuilla is currently under development that is supposed to support T-Bird access to Exchange native protocol, but it is in beta and only available for Windows version of T-Bird.

Configuring Evolution is not particularly hard, but you should be aware that its e-mail storage format is not compatible with T-Bird's. You will have to decide on the one or the other.

---

### Post by Dmal on 2013-04-10
Hi guys,


as you can see on the [screenshot]("http://ge.tt/1OC6wgd/v/0") , 'ExQuilla'  IS AVAILABLE also for Linux.


You can download 'ExQuilla' addon from the Mozilla official site ( [https://addons.mozilla.org/en-US/thunderbird/addon/exquilla-exchange-web-services](https://addons.mozilla.org/en-US/thunderbird/addon/exquilla-exchange-web-services) ) . 

You can also download 'ExQuilla' addon from developer's site ( [https://exquilla.zendesk.com/home](https://exquilla.zendesk.com/home) )  ... which is more up to date ( 20th February 2013 ).


Regards.

---


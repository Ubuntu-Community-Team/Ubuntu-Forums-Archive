---
title: "Voip with Linphone and G729"
date: 2013-03-28
forum: Packaging and Compiling Programs
---

### Post by Smetsers on 2013-03-28
I have a very slow internet connection so therefore I'd like to use the G729 audio codec with Linphone and Voipbuster (actually I'd prefer to use Ekiga but this isn't available for Quantal Quetzal 12.10 and has no G729). Apparently it should be possible to use G729 with Linphone, see [here]("http://www.linphone.org/eng/documentation/dev/bcg729.html"). I downloaded the tar.gz file and followed installation instructions. There appear some *« as far as I know »* codec files in /usr/local/lib but the codec doesn't appear in Linphone. I can't find anywhere how to solve this. Does anybody know how to get the G729 codec working in Linphone?

---

### Post by wistle on 2013-06-13
You can try installing linphone from the PPA, which includes the codec plugins:
 
[https://launchpad.net/~michael-gruz/+archive/linphone/+build/4475948](https://launchpad.net/~michael-gruz/+archive/linphone/+build/4475948)

Charl

---


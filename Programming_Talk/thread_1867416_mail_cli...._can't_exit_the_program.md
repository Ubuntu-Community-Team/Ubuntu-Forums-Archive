---
title: "mail cli.... can't exit the program"
date: 2011-10-22
forum: Programming Talk
---

### Post by wannabegeek on 2011-10-22
hi all...

I have a small problem that I can't find a google answer for.....it's so simple it's a little hard to explain...

I have been using mail:

```
mail -s "testing" --append=FROM:"test subject line" foo@bar 
```

I get the cc: prompt which I leave blank, then  I compose the body of the message....
To exit the program and send the mail, I thought that all I do, is skip a line by pressing enter,

type a  period (.)  then inter again....nothing happens...I figured how to interrupt :)

thanks !

wbg

---

### Post by wannabegeek on 2011-10-22
I found a nixcraft blog with some info..

[http://www.cyberciti.biz/faq/howto-write-command-to-send-receive-mail/](http://www.cyberciti.biz/faq/howto-write-command-to-send-receive-mail/)

So control -D sent my mail...not  the dot following blank space..... and not the behavior I expected from the nixcraft
article....

I guess I can live with Control D , now I need to figure out how to get mail to download my gmail mail if that's possible...

---


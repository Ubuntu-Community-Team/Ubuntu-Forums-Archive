---
title: "Send data not text over serial"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by Commander_Bob on 2008-09-20
I have an AVR that I want to send data to over serial. I would normally use echo but that sends ascii characters and I want numbers. I need to send
0x00
0x00
0x00
0xXX
0xXX
0xXX
where XX changes.

Also how do I set up the serial port from the command line? 

Thanks,
Justin

---

### Post by cmnorton on 2008-09-21
You will need a dialer application, either open source or proprietary. 

It sounds like you do not need the ability to do sophisticated key mapping. That is the main reason I purchased and am happy with Ericom's PowerTerm Interconnect for Linux, but it's in the $150/$160 range with $20-ish annual support. 

You can download PowerTerm for Linux; it has a 30-day trial period. I'd be interested in knowing what open source stuff you find. It's always good to know these things.

---

### Post by Commander_Bob on 2008-09-21
I ended up making my own program in C. It works a lot better then what I could of done with bash, as I don't know bash but am very familiar with C. You can check it out at [http://www.youtube.com/watch?v=VJy4qKV9h9E]("http://www.youtube.com/watch?v=VJy4qKV9h9E").
If you want the code I can send it to you.

---

### Post by cariboo on 2008-09-21
Have you had a look at minicom, or cutecom they are both available in the rpositories.

Jim

---

### Post by Commander_Bob on 2008-09-21
I was originally using minicom but you can only send ascii charaters and I needed to send integers.

---


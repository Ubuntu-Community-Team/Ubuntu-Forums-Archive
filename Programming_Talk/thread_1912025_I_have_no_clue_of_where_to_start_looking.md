---
title: "I have no clue of where to start looking"
date: 2012-01-19
forum: Programming Talk
---

### Post by mrhobbeys on 2012-01-19
I would like to program some software that acts as a back-end to process input that will be converted from an analog signal to digital, and then sent back to be converted from digital to analog.

How can I simulate inputs so that I can make changes to the program I have made?

Any good ways to convert digital to analog and visa versa?

Basically as of now I have HTML and PHP that I think does what I want but I am trying to convert it to python. 

I'm really sorry if I have not included enough information just let me know. I would be happy to explain the project in detail if needed.

---

### Post by Arndt on 2012-01-20
> **mrhobbeys said:**
> I would like to program some software that acts as a back-end to process input that will be converted from an analog signal to digital, and then sent back to be converted from digital to analog.

How can I simulate inputs so that I can make changes to the program I have made?

Any good ways to convert digital to analog and visa versa?

Basically as of now I have HTML and PHP that I think does what I want but I am trying to convert it to python. 

I'm really sorry if I have not included enough information just let me know. I would be happy to explain the project in detail if needed.

I'm not an expert in this field, and seldom have to do with hardware or analog signal processing. I usually associate analog signals with hardware (microphones, sound cards, for example), and the only thing the software ever sees is the digitized version, so I'm not sure what you mean. This is probably a naive view, but as no one has answered for 7 hours..

How does the signal get to the program?

---

### Post by CoffeeRain on 2012-01-20
Yes, further explanation of the project might help. Analog could mean anything really.

---

### Post by ofnuts on 2012-01-20
> **mrhobbeys said:**
> I would like to program some software that acts as a back-end to process input that will be converted from an analog signal to digital, and then sent back to be converted from digital to analog.

How can I simulate inputs so that I can make changes to the program I have made?

Any good ways to convert digital to analog and visa versa?

Basically as of now I have HTML and PHP that I think does what I want but I am trying to convert it to python. 

I'm really sorry if I have not included enough information just let me know. I would be happy to explain the project in detail if needed.
Your average computer won't handle analog signals... unless these fall in the audio range in which case the audio I/O subsystem could be coerced into using them, but some restrictions may apply. Your software will in any case only see the digital version, there are specialized chips to do the conversion..

Otherwise you'll find analog I/O adapters (on USB)(see Arduino for some low-cost solutions) but Linux support for these isn't guaranteed.

---


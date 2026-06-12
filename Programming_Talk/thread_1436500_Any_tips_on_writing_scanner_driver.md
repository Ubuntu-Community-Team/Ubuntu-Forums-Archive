---
title: "Any tips on writing scanner driver?"
date: 2010-03-22
forum: Programming Talk
---

### Post by paulnewall on 2010-03-22
I'm interested in writing a scanner driver for the scanner in the Kodak 5250 AiO printer.
Does anyone have ideas how to start? Are there loads of possible protocols? or only a few?
Does anyone kn ow if this scanner is similar to another one for which there is already a linux driver?

---

### Post by Goveynetcom on 2010-03-22
> **paulnewall said:**
> I'm interested in writing a scanner driver for the scanner in the Kodak 5250 AiO printer.
Does anyone have ideas how to start? Are there loads of possible protocols? or only a few?
Does anyone kn ow if this scanner is similar to another one for which there is already a linux driver?
Well, not knowing exactly how to do this (but willing to point you in my opinion of a good start) try doing some research in general fields for this like I would think you would look at developing drivers, probably understanding assembly (assuming that is what you're coding in, I have read around and a lot of people *seem *to write them in it), I would maybe go even as far as possibly contacting an employee or someone who has worked on something similar to this (if possible). I personally would take a driver (like a printer driver) and run it through a disassembler (like IDA) and study and mess with the decoded assembly. With something as complicated as this I would possibly enlist the help of some others interested in helping ;).

Don't know if that was what you were thinking or that you think I am totally off, but that is my guess as to how to tackle this beast...

Oh, also look for some possible schematics of the printer so you can try writing code to interact with the individual pieces.

Hope that helps :popcorn: ...

And good luck!

---

### Post by pbrane on 2010-03-23
You really need to know what chipset your scanner uses. You can't write a driver without knowing how to setup and control the device. Then you need to know how to write a linux device driver. Lots to learn if you've never done it. Start with learning about the scanner hardware, then design a driver, then you can implement it.

---


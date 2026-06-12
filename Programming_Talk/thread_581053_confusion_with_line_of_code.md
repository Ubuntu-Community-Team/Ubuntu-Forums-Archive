---
title: "confusion with line of code"
date: 2007-10-19
forum: Programming Talk
---

### Post by renzokuken on 2007-10-19
hi

i'm having to write a script to control a piece of experimental equipment using its built in ADL language (SAX Basic => Visual Basic with a few custom functions).

in the code block below, what is the red line doing w.r.t. to the IF <> part?

the code creates a new data continuum then the startinst command starts a scan and puts the data recorded by the spectrometer into that continuum. but i'm confused as to what **<> 0** means

```

Sub PointScan
		NewCtm("MyData")
	[color=red]If StartInst("MyData") <> 0 Then[/color]
		While ScanningInst
			DoEvents()
		Wend
	End If
end sub

```

ps, sorry if its a dumb question, i've been thrown into writing this program at the deepend

---

### Post by CptPicard on 2007-10-19
Well, typically <> 0 means a test for value being nonzero... although visual basic is not really something I am familiar with.

---

### Post by renzokuken on 2007-10-19
so its checking if MyData actually exists, and if it does, then it continues??????

---

### Post by jespdj on 2007-10-19
> **renzokuken said:**
> so its checking if MyData actually exists, and if it does, then it continues??????
It checks if the call StartInst("MyData") returns a value that is non-zero. What that means exactly depends on what the function StartInst does.

---


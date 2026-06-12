---
title: "Using data returned from a function [Python]"
date: 2009-12-23
forum: Programming Talk
---

### Post by jSalv on 2009-12-23
Good day to all of you,

First of all, I'm new here, so if I'm posting this in an incorrect section, please tell me.

But my question (about Python) is the following:
How can I, after having called a variable, use the data returned?

For example, in a button, defined as in Fig. 1, I have used the function defined in Fig. 2. How can I use the data returned by this function (I have tried as in Fig. 3, but it gives me an error).

Fig. 1:
```

newMobButton = wx.Button(panel, label="Find new monster", pos=(360, 30), size=(100, 25))
		self.Bind(wx.EVT_BUTTON, self.findNew, newMobButton)

```

Fig. 2:
```

def findNew(self, event):
		rnd = randrange(0, 11)
		mobNames = [
			'Goblin worker',
			'Goblin soldier',
			'Goblin king',
			'Orc worker',
			'Orc soldier',
			'Orc king',
			'Human worker',
			'Human soldier',
			'Human paladin',
			'Human king',
			'Elf king'
			]
		mobHPs = [
			randrange(40, 60),
			randrange(70, 90),
			randrange(130, 160),
			randrange(100, 120),
			randrange(150, 170),
			randrange(210, 230),
			randrange(70, 90),
			randrange(120, 140),
			randrange(150, 170),
			randrange(200, 220),
			randrange(160, 200),
			]
		mobDMGs = [
			randrange(2, 4),
			randrange(3, 5),
			randrange(4, 7),
			randrange(3, 6),
			randrange(5, 8),
			randrange(6, 10),
			randrange(4, 7),
			randrange(5, 9),
			randrange(6, 10),
			randrange(6, 13),
			randrange(5, 15)
			]
		mobDEFs = [
			randrange(0, 2),
			randrange(1, 2),
			randrange(2, 4),
			randrange(1, 3),
			randrange(2, 5),
			randrange(3, 6),
			randrange(1, 2),
			randrange(3, 5),
			randrange(4, 7),
			randrange(5, 10),
			randrange(3, 11)
			]
		mob = mobNames[rnd]
		an = "a "
		if str(mob).startswith('A'): an = "an "
		if str(mob).startswith('E'): an = "an "
		if str(mob).startswith('I'): an = "an "
		if str(mob).startswith('O'): an = "an "
		if str(mob).startswith('U'): an = "an "
		return [an, mobNames[rnd], mobHPs[rnd], mobDMGs[rnd], mobDEFs[rnd]]

```
The return statement of this function I feel is wrong, but it might be me that is now.

Fig. 3:
```

btnOutput = self.Bind(wx.EVT_BUTTON, self.findNew, newMobButton)
		wx.StaticText(panel, -1, "You are fighting " + btnOutput[0] + btnOutput[1] + ".")

```
This was like Fig. 1, but added a variable where to store this. This seems so wrong I don't know even why I tried.

Any help is greatly appreciated.
Thanks!!

Jose

---

### Post by -grubby on 2009-12-23
I don't think I'm fully understanding. Is this what you meant?

```

def test_function():
    return "Something"

print test_function() # prints "Something"

```

---

### Post by jSalv on 2009-12-24
More or less that is what I mean, but I would not like to print the output, but create a StaticText with parts of the outcoming list.

So, something like this:

```

wx.StaticText(panel, -1, output[0] + output[1], ...)
wx.StaticText(panel, -1, output[2], ...)
#etc...

```

---


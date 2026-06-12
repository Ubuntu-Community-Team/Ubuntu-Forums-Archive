---
title: "Gedit custom spice.lang"
date: 2013-01-09
forum: Programming Talk
---

### Post by bubulescu on 2013-01-09
Hello

I am currently trying to make a personal variant of syntax highlighting for SPICE (LTspice), working in gedit (2.30.4, LM14 Xfce, x64). Going through gedit's *.lang files for the first time I managed to get them working, but there still are things that elude me.

For this particular case, there's a SPICE element (device), that starts with letter A in the netlist -- A-device --, it has 8 pins that can be connected to various net names, then a descriptor (id, model) and possible other parameters. Here's an example:
```

Az#3 a {if(a,1,0)} { if( b, 2, 0 ) } 1 N001 0 Q _Q AND vhigh=1 td=1n

```
with the following explanations:

```
Az#3
```
 - the name is always at the beginning of the line and can have letters, numbers, characters assigned to it, but with no spaces.

```
a {if(a,1,0)} { if( b, 2, 0 ) } 1 N001 0 Q _Q
```
 - the 8 pins, connected to nets bearing letters, numbers, characters:
 pin 1 - connected to net 'a'
 pin 2 - conditionally connected to either '1' or ground as a function of some parameter 'a'
 pin 3 - also conditional, but it has spaces
 pin 4 - connected to net '1'
 pin 5 - connected to net N001 (generic autoassigned name)
 pin 6 - grounded
 pin 7 - output Q
 pin 8 - complementary output _Q

```
AND
```
 - model's name

```
vhigh=1 td=1n
```
 - various parameters


What I want is to apply color#1 to the name, color#2 to the pins, color#1 to the model's name and default (black/white/...) to the rest. This is what I have for this part:

```

	<!-- A-devices -->
	<context id="A-devices" style-ref="type">
		<start>^A\S*\s+</start>
		<end>(and|buf|dflop|inv|modulate|or|phasedet|samplehold|schmitbuf|schmitinv|schmitt|srflop|varistor|xor)</end>
		<include>
			<context id="A-character" style-ref="decimal">
				<match>((\S+|\{ \N+ \})\s+){8}</match>
			</context>
		</include>
	</context>

```

with "type" and "decimal" chosen to match the colors. As you can see, the pins can have spaces if and only if they are enclosed within curled braces. Now, the <match> part is the one not working: it searches for either one-block characters (\S), or for anything within '{}', then adds one or more spaces after and multiplies it by 8. This should correctly detect whatever characters there are between the name and the model's name, but it fails to do so whenever there are spaces whithin brackets, the spaces act like delimiters for the next pin; else, it works. I have tried quite a few approaches, '[]', '()', '.', ('{)? [^\t]+ (?(1)\}), to name a few, variants, can't make it work.

So, my question is: can this be done and, if yes, can someone please help me get this done?


Anticipated thanks,
Vlad

---

### Post by bubulescu on 2013-01-11
I have managed to do it, after many combinations and some more surfing for clues: [Paul Dixon's post]("http://stackoverflow.com/questions/413071/regex-to-get-string-between-curly-braces-i-want-whats-between-the-curly-brace") which wouldn't work at first but then I thought I'd reverse the choice order:
```
<match>((\{[^}]+\}|\S+)\s+){8}</match>
```

It correclty works now matter what I throw at it.

---


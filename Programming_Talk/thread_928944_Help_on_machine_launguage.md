---
title: "Help on machine launguage"
date: 2008-09-24
forum: Programming Talk
---

### Post by cris84 on 2008-09-24
hi i have see and try all but i cant find the problem.. help

		ORG	$8000
NUMBERS		DC.B	36,128,0,48,76,30,225,0,0,177,55,208,0,0,77,200,0,30,149,245
		DC.B	3,140,40,129,38,199,99,180,81,0,65,77,148,253,166,129,0,216,15,0
TOTALODD	DS.W	1

		ORG	$8100
ODDNUM		MOVEA.L	#NUMBERS,A2
		CLR.B	D4
		CLR.B	D2
		CLR.B	D0
		MOVE.W	#8027,D1

CHECKIT		DTVU	#2,D2
		CMP.B	#0,D2
		BEQ	NEXT
		CMP.B	#1,D2
		BNE	CHECKIT
		ADD.B	#1,D0
		MOVE.B	-(A2),D4
		ADDA.L	#1,A2
		MOVE.W	D0,TOTALODD
		TRAP	#3
		TRAP	#9

NEXT		DBRA	D1,CHECKIT
		RTS



25 lines process
0 warning
1 fatal

help why got 1 fatal?

---

### Post by Zugzwang on 2008-09-25
Dear OP (original poster),

[LIST]
[*] Whenever you get an error, make sure to copy & paste the error message in a precise way. In this case, it appears as if you did not do this. Reason: [...**What is the fatal error?**...]
[*] The context of your post is not given. For example, make sure that for all programming related questions, you mention the used programming language (if applicable), the type of processors assembly code is intended to run on (for example, x86, 64 bit) and the dialect of the language you used (for example, for the programming language C, C99). Also explain all abbreviations that are not common in the general programming talk context (example: When using the abbreviation "PSX", you might want to state that you are meaning "Playstation portable"). In this case it seems like you forgot: [..**The processor/system architecture you are using, the assembly dialect, the assembler used**...]
[/LIST]

---

### Post by lisati on 2008-09-25
The code doesn't look like any x86 code I've seen, what processor is it for?

---


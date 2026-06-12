---
title: "procedural psuedocode to check a sentence if it is a pangram"
date: 2011-04-14
forum: Programming Talk
---

### Post by Thandokazi on 2011-04-14
:confused:
[SIZE=3][FONT=Calibri]**string**:          sentence        ;[/FONT][/SIZE]
[FONT=Calibri][SIZE=3][/SIZE][/FONT][FONT=Calibri][SIZE=3][/SIZE][/FONT][SIZE=3][FONT=Calibri]**characte****r**:    current         ,[/FONT][/SIZE]
[FONT=Calibri][SIZE=3][/SIZE][/FONT][SIZE=3][FONT=Calibri]   userResponse    ;[/FONT][/SIZE]
[FONT=Calibri][SIZE=3][/SIZE][/FONT][SIZE=3][FONT=Calibri]**integer**:    counter     ,[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]   notCrossedout  ;[/FONT][/SIZE]
[FONT=Calibri][SIZE=3][/SIZE][/FONT][SIZE=3][FONT=Calibri]DO[/FONT][/SIZE]
[FONT=Calibri][SIZE=3][/SIZE][/FONT][SIZE=3][FONT=Calibri]Get (keyboard, **REFERENCE****:   **sentence    ) ;[/FONT][/SIZE]
[FONT=Calibri][SIZE=3][/SIZE][/FONT][SIZE=3][FONT=Calibri]FOR    current    GOES FROM 'A' TO 'Z' ;[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Write      current[/FONT][/SIZE]
[FONT=Calibri][SIZE=3][/SIZE][/FONT][FONT=Calibri][SIZE=3][/SIZE][/FONT][SIZE=3][FONT=Calibri]ENDFOR[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]FOR      counter     GOES FROM 0 TO Length (    sentence    ) -1[/FONT][/SIZE]
[FONT=Calibri][SIZE=3][/SIZE][/FONT][FONT=Calibri][SIZE=3][/SIZE][/FONT][SIZE=3][FONT=Calibri]current    &#8592; sentence  [    counter    ] ;[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Cross off letter on the paper that matches current letter  ;[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]ENDFOR[/FONT][/SIZE]
[FONT=Calibri][SIZE=3][/SIZE][/FONT][SIZE=3][FONT=Calibri]notCrossedOut     &#8592; 0 ;[/FONT][/SIZE]
[FONT=Calibri][SIZE=3][/SIZE][/FONT][SIZE=3][FONT=Calibri]FOR            current    GOES FROM 'A' TO 'Z' ;[/FONT][/SIZE]
[FONT=Calibri][SIZE=3][/SIZE][/FONT][SIZE=3][FONT=Calibri]        IF (   current     not crossed out)[/FONT][/SIZE]
[FONT=Calibri][SIZE=3][/SIZE][/FONT][FONT=Calibri][SIZE=3][/SIZE][/FONT][SIZE=3][FONT=Calibri]notCrossedOut    &#8592;       notCrossedOut       + 1 ;[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]       ENDIF[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]ENDFOR[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]IF     (notCrossedOut = 0)[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]         Display ('Sentence is a pangram')  ;[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]ELSE[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]        Display ('Sentence is NOT a pangram') ;[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]ENDIF[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Display ('Do you want to test another sentence? Y/N') ;[/FONT][/SIZE]
 
 
Is there any one who can help me with this code to change it to a procedural psuedocode? plz help its urgent!

---

### Post by NovaAesa on 2011-04-18
It looks all procedurey and pseudocodey already :P

---


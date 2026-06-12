---
title: "Java Bytecode Decompiler"
date: 2007-01-18
forum: Programming Talk
---

### Post by phossal on 2007-01-18
I need recommendations on a good Java bytecode decompiler. I've already googled it. I've already used a few. I would like to know if any of you have used one successfully and would *recommend* it. And why.

xiexie

---

### Post by amo-ej1 on 2007-01-18
the only one i've ever played with was JAD: [http://www.kpdus.com/jad.html](http://www.kpdus.com/jad.html)  no real reason, it was the first one I found and it did it's job. But I don't seem to find it in the ubuntu repositories ...

---

### Post by ZylGadis on 2007-01-18
Why do you need a decompiler? Java bytecode is almost source level.

---

### Post by phossal on 2007-01-18
What?

---

### Post by Ramses de Norre on 2007-01-18
> **ZylGadis said:**
> Why do you need a decompiler? Java bytecode is almost source level.

You call this almost source level:
```
KijkAlgoritmejava/lang/Object<init>()VCode

        LineNumberTableLocalVariableTablethisLKijkAlgoritme;kijkKijker;[[LZichtElement;)V
                                                                                                   Kijker
                                                                                                              geefY()I
                                                                                                                           
                                                                                                                             geefX
                                                                                                                                     
                                                                                                                                       ziet(LZichtElement;II)V

      startScan(LKijker;)Ljava/util/Vector;
"
  #$doeScan>(Ljava/util/Vector;LKijker;[[LZichtElement;)Ljava/util/Vector;
&('java/util/Vector
                     )sizekijkerLKijker;wereld[[LZichtElement;scanLjava/util/Vector;LocalVariableTypeTable!Ljava/util/Vector<LScanElement;>;   Signature+(LKijker;)Ljava/util/Vector<LScanElement;>;
&       6
          ScanElement
58
  9(IIIIIIIIIII)V
 & ;
     < = 
&#9618;&#9229;&#9229;E&#9484;&#9226;&#9492;&#9226;&#9532;&#9500; (L&#9496;&#9618;&#9524;&#9618;/&#9484;&#9618;&#9532;±/O&#9225;&#9496;&#9226;&#9228;&#9500;;)V
 5 ?
      @ 
         (IIIIIIIII)V &#9474; I &#8804; \(L&#9496;&#9618;&#9524;&#9618;/&#9508;&#9500;&#9227;&#9484;/V&#9226;&#9228;&#9500;&#9146;&#9148;<LS&#9228;&#9618;&#9532;E&#9484;&#9226;&#9492;&#9226;&#9532;&#9500;;>;LK&#9227;&#9496;&#9488;&#9226;&#9148;;[[LZ&#9227;&#9228;&#9252;&#9500;E&#9484;&#9226;&#9492;&#9226;&#9532;&#9500;;)L&#9496;&#9618;&#9524;&#9618;/&#9508;&#9500;&#9227;&#9484;/V&#9226;&#9228;&#9500;&#9146;&#9148;<LS&#9228;&#9618;&#9532;E&#9484;&#9226;&#9492;&#9226;&#9532;&#9500;;>;
 & F
     G H       &#9226;&#9484;&#9226;&#9492;&#9226;&#9532;&#9500;A&#9500; (I)L&#9496;&#9618;&#9524;&#9618;/&#9484;&#9618;&#9532;±/O&#9225;&#9496;&#9226;&#9228;&#9500;;        5 J
                                                             C B         5 L
                                                                             A B
 & N
     O H &#9148;&#9226;&#9492;&#9146;&#9524;&#9226;        5 Q
                             R B &#9229;&#9227;&#9148;X  5 T
                                             U B &#9229;&#9227;&#9148;Y
                                                        W Y X 
                                                               Z&#9227;&#9228;&#9252;&#9500;E&#9484;&#9226;&#9492;&#9226;&#9532;&#9500;
                                                                            Z [ &#9225;&#9484;&#9146;&#9488;&#9488;&#9226;&#9226;&#9148;&#9500;Z&#9227;&#9228;&#9252;&#9500; 
                                                                                                 (LK&#9227;&#9496;&#9488;&#9226;&#9148;;)Z     5 ]
                                                                                                                     ^ B &#9229;     5 &#9670;
                                                                                                                                     &#9618; B &#9227;&#9532;&#9228;NE  5 &#9228;
                                                                                                                                                     &#9229; B &#9227;&#9532;&#9228;E  5 °
                                                                                                                                                                     ± B &#9149;&#9484;&#9146;&#9147;&#9226;XE     5 &#9227;
    &#9496; B &#9149;&#9484;&#9146;&#9147;&#9226;YE         5 &#9484;
                             &#9492; B&#9149;&#9484;&#9146;&#9147;&#9226;XNE        5 &#9146;
                                                     &#9147; B&#9149;&#9484;&#9146;&#9147;&#9226;YNE
  &#9148;
     &#9149; &#9500; &#9532;&#9226;&#9516;S&#9228;&#9618;&#9532;E&#9484;&#9226;&#9492;&#9226;&#9532;&#9500; (IILK&#9227;&#9496;&#9488;&#9226;&#9148;;IIZ)LS&#9228;&#9618;&#9532;E&#9484;&#9226;&#9492;&#9226;&#9532;&#9500;;  5 &#9524;
                                                             &#9516; &#9474; &#9226;&#9532;&#9229; Z       &#8805; &#8800; &#960; &#9496;&#9618;&#9524;&#9618;/&#9484;&#9618;&#9532;±/S&#8804;&#9149;&#9500;&#9226;&#9492;
                                                                                                          £ · &#9146;&#9508;&#9500; L&#9496;&#9618;&#9524;&#9618;/&#9227;&#9146;/P&#9148;&#9227;&#9532;&#9500;S&#9500;&#9148;&#9226;&#9618;&#9492; € !&#9226;&#9148;&#9148;&#9146;&#9148;
 ‚ „ ƒ &#9496;&#9618;&#9524;&#9618;/&#9227;&#9146;/P&#9148;&#9227;&#9532;&#9500;S&#9500;&#9148;&#9226;&#9618;&#9492;
LS&#9228;&#9618;&#9532;E&#9484;&#9226;&#9492;&#9226;&#9532;&#9500;; &#9484;&#9618;&#9149;&#9500; LZ&#9227;&#9228;&#9252;&#9500;E&#9484;&#9226;&#9492;&#9226;&#9532;&#9500;; &#9532;&#9226;&#9474;&#9500; L&#9496;&#9618;&#9524;&#9618;/&#9484;&#9618;&#9532;±/S&#9500;&#9148;&#9227;&#9532;±;)V&#9532;&#9226;&#9474;&#9500;S&#9228;&#9618;&#9532; &#9228;&#9508;&#9148;&#9148;&#9226;&#9532;&#9500; 
                                             &#9227;±&#9532;&#9146;&#9148;&#9226;F&#9227;&#9148;&#9149;&#9500;&#9532;&#9226;&#9516;S&#9500;&#9618;&#9148;&#9500; &#9225;&#9484;&#9146;&#9228;&#9488;&#9226;&#9229; &#9532;&#9226;&#9516;E&#9532;&#9229; &#9148;&#9226;&#9149; &#9532;X &#9532;Y &#9229;&#9474; &#9229;&#8804; &#9500;&#9146;&#9147; &#9229;&#9508;&#9492;&#9492;&#8804; 
S&#9146;&#9508;&#9148;&#9228;&#9226;F&#9227;&#9484;&#9226; K&#9227;&#9496;&#9488;A&#9484;±&#9146;&#9148;&#9227;&#9500;&#9492;&#9226;.&#9496;&#9618;&#9524;&#9618; !               /     *·±    
        
              
                   
          &#65533;8*+*&#65533;2*&#65533;2*&#65533;*&#65533;&#65533;*&#65533;M&#65533;
,*+&#65533;!M,&#65533;%&#65533;&#65533;&#65533;&#65533;
!      &
0
7
  8*+8,-&./0
                &.1
 23f    à» &Y· 4L*¹  =*¹  >+» 5Y&#9229;&#9229;· 7¶ :+» 5Y&#9670;&#9229;· >¶ :+» 5Y&#9670;&#9229;· 7¶ :+» 5Y&#9670;&#9670;· >¶ :+» 5Y&#9670;&#9670;· 7¶ :+» 5Y&#9229;&#9670;· >¶ :+» 5Y&#9229;&#9670;· 7¶ :+» 5Y&#9229;&#9229;· >¶ :+°    
   2 
          0Hbz&#65533;&#65533;&#65533;&#65533;
                               *&#65533;*&#65533;./&#65533;AB&#65533;CB0
                                                 &#65533;.1
#$2DcY&#65533;&Y&#65533;4N**&#65533;%d&#65533;E&#65533;5:,&#65533;I2&#65533;K2:*&#65533;M&#65533;5:*&#65533;M&#65533;5:,&#65533;I2&#65533;K2&#65533;&#65533;66   &#65533;P6
&#65533;S6
     &#65533;&#65533;:
&#65533;&#65533;&#65533;\&#65533;;&#65533;_&#65533;3Y&#65533;\&#65533;b`&#65533;\Y&#65533;K&#65533;e`&#65533;KY&#65533;I&#65533;h`&#65533;I&#65533;0Y&#65533;\&#65533;_`&#65533;\Y&#65533;K&#65533;k`&#65533;KY&#65533;I&#65533;n`&#65533;I:
                                                                                            :
`      
+,     22     &#65533;&#65533;&#65533;&#65533;122+&#65533;V6
`      
&#65533;q&#65533;K&#65533;&#65533;&#65533;     &#65533;I&#65533;&#65533;&#65533;22+&#65533;V6
   &#65533;l  +

 &#65533;q:
      ´ K´ K  
                 ´ I´ IŸ -
                            &#65533;:-¶ ::
                                     § 1
&#9670;      
š ´ K ÿÆ    ´ I ÿ¼2+¹ V 6
    Ç         +

 ¸ &#9472;:
      ´ K ÿ
š ž´ &#9508;™ –I ÿ 
            Æ ‘´ \ 3Y´ \´ &#9225;&#9670;µ \Y´ K´ &#9226;&#9670;µ KY´ I´ &#9252;&#9670;µ I§ 0Y´ \´ _&#9670;µ \Y´ K´ &#9488;&#9670;µ KY´ I´ &#9532;&#9670;µ I
                                                                                                                     ´ K´ K  
                                                                                                                                 ´ I´ IŸ -
                                                                                                                                             &#65533;:-&#65533;::
                                                                                                                                                      :
                                                                                                                                                        &#65533;u&#65533;*&#65533;%&#65533;*&#65533;M&#65533;5:&#65533;:&#65533;:&#65533;y&#65533;&#65533;&#65533;&#65533;M&#65533;5:&#65533;P6
&#65533;S6
     &#65533;&#65533;-&#65533;
>O%&&'0(:)S*V+Y,`-g.j/m0&#65533;1&#65533;2&#65533;4&#65533;6&#65533;8&#65533;9&#65533;:&#65533;;&#65533;<&#65533;=&#65533;?
`[7bAcPJdfvg~h&#65533;i&#65533;j&#65533;l&#65533;m&#65533;n&#65533;p&#65533;q&#65533;rtvwx#y){-|5~:D&#65533;K&#65533;R.W&#65533;rO&#65533;P&#65533;K&#65533;R&#65533;S&#65533;U&#65533;V&#65533;W&#65533;Y&#65533;[&#65533;]&#65533;^&#65533;_
                                                                                   &#65533;Y./Y*+Y,-Q&#65533;/B&#65533;&#65533;&3&#65533;&#65533;:&#65533;&#65533;S&#65533;xVAYCB    `&#65533;RB
g&#65533;UB
     m&#65533; &#65533;
&#65533;)&#65533;&#65533; 0      Y . 1  Q ‡ 1  
   ¬:6™ &#9229;6&#9229;,¹  &#9229;6        ,¹  &#9229;6
6
       œ      &#9500;6      6
                          §   š ™ § &#9500;6
                                            6
                                              
œ 
&#9500;6
6
  § 
š ™§ &#9500;6
             6
 66š ;
6     6
6       6
™ 
         § § 
                   &#65533;&#65533;6&#65533;#&#65533;
                                 &#65533;&#65533;&#65533;
                                         Ÿ § 6™ 0        
&#9229;6            ``6
d
dd6
       `6
          `&#65533;V  
d6            `d6
d
`6&#9670;§ `6`6
              `6
               `&#65533;!&#65533;5Y
  
 · >:§ !» 5Y
  
   · 7:°    
   â 8   Š  Œ         Ž      ’ & “ 1 ” 4 • 9 – > — D ˜ I ™ V › Y œ ^  &#9228; ž &#9227; Ÿ &#9532;   £ ¢ € £ „ ¨ ‡ ª ‹ «  ¬ ’ * – ® š ¯ ž ° Ã ² ã ´ è µ ï ¶ ø · ¸
                                                                                                                                                           ¹ » ¼% ½1 ¿; ÀB ÁI ÂS ÄZ Å&#9618; Æ&#9252; Ê&#9492; Ë&#960; Ìƒ Ë‹ Î– Ïœ Ð¤ Î© Ò 
                                                      è   ¬ A B    ¬ C B   ¬ * +   ¬ R B   ¬ U B   ¬ &#9516; &#9474;  © ‘ ‰  ¦ ’ B          £ “ B &† ” B   1&#960; • B 
 4&#9474; &#9492; B 
          YS &#9147; B 
 „( &#9496; B  ï & ^ B &#65533;^B&#65533;dB%&#65533;dBaB1{aB&#65533;%&#65533;x&#65533;-&#65533;B&#65533;&#65533;r
```
It's the bytecode for a class of 212 lines.

---

### Post by ZylGadis on 2007-01-18
Weird, this is how bytecode looks here:

```

00000000  ca fe ba be 00 00 00 32  00 c1 0a 00 24 00 63 0a  |.......2....$.c.|
00000010  00 0c 00 64 0a 00 0c 00  65 08 00 66 0a 00 67 00  |...d....e..f..g.|
00000020  68 0b 00 69 00 6a 0a 00  0c 00 6b 0a 00 0c 00 6c  |h..i.j....k....l|
00000030  0a 00 23 00 6d 07 00 6e  0a 00 0a 00 63 07 00 6f  |..#.m..n....c..o|
00000040  09 00 23 00 70 0a 00 0c  00 71 0a 00 72 00 73 0b  |..#.p....q..r.s.|
00000050  00 74 00 75 0b 00 76 00  77 0b 00 74 00 78 07 00  |.t.u..v.w..t.x..|
00000060  79 0a 00 13 00 7a 0b 00  7b 00 7c 0b 00 7d 00 7e  |y....z..{.|..}.~|
00000070  0b 00 7d 00 7f 07 00 80  0b 00 18 00 81 0b 00 82  |..}.............|
00000080  00 83 0b 00 18 00 84 0b  00 69 00 7c 07 00 85 07  |.........i.|....|
00000090  00 86 07 00 87 0a 00 1f  00 8a 0b 00 1e 00 8b 08  |................|
000000a0  00 8c 07 00 8d 07 00 8e  07 00 8f 01 00 04 6e 61  |..............na|
000000b0  6d 65 01 00 12 4c 6a 61  76 61 2f 6c 61 6e 67 2f  |me...Ljava/lang/|
000000c0  53 74 72 69 6e 67 3b 01  00 06 3c 69 6e 69 74 3e  |String;...<init>|
000000d0  01 00 03 28 29 56 01 00  04 43 6f 64 65 01 00 0f  |...()V...Code...|
000000e0  4c 69 6e 65 4e 75 6d 62  65 72 54 61 62 6c 65 01  |LineNumberTable.|
000000f0  00 12 4c 6f 63 61 6c 56  61 72 69 61 62 6c 65 54  |..LocalVariableT|
00000100  61 62 6c 65 01 00 04 74  68 69 73 01 00 0b 4c 44  |able...this...LD|
00000110  54 4f 46 69 6e 64 65 72  3b 01 00 0d 63 6f 6e 73  |TOFinder;...cons|
00000120  74 72 75 63 74 54 72 65  65 01 00 21 28 4c 6a 61  |tructTree..!(Lja|
00000130  76 61 2f 69 6f 2f 46 69  6c 65 3b 4c 6a 61 76 61  |va/io/File;Ljava|
00000140  2f 75 74 69 6c 2f 4c 69  73 74 3b 29 56 01 00 01  |/util/List;)V...|
00000150  66 01 00 0e 4c 6a 61 76  61 2f 69 6f 2f 46 69 6c  |f...Ljava/io/Fil|
00000160  65 3b 01 00 04 61 72 72  24 01 00 0f 5b 4c 6a 61  |e;...arr$...[Lja|
00000170  76 61 2f 69 6f 2f 46 69  6c 65 3b 01 00 04 6c 65  |va/io/File;...le|
00000180  6e 24 01 00 01 49 01 00  02 69 24 01 00 07 63 75  |n$...I...i$...cu|
00000190  72 72 65 6e 74 01 00 04  6c 69 73 74 01 00 10 4c  |rrent...list...L|
000001a0  6a 61 76 61 2f 75 74 69  6c 2f 4c 69 73 74 3b 01  |java/util/List;.|
000001b0  00 16 4c 6f 63 61 6c 56  61 72 69 61 62 6c 65 54  |..LocalVariableT|
000001c0  79 70 65 54 61 62 6c 65  01 00 20 4c 6a 61 76 61  |ypeTable.. Ljava|
000001d0  2f 75 74 69 6c 2f 4c 69  73 74 3c 4c 6a 61 76 61  |/util/List<Ljava|
000001e0  2f 69 6f 2f 46 69 6c 65  3b 3e 3b 01 00 0d 53 74  |/io/File;>;...St|
000001f0  61 63 6b 4d 61 70 54 61  62 6c 65 07 00 34 01 00  |ackMapTable..4..|
00000200  09 53 69 67 6e 61 74 75  72 65 01 00 31 28 4c 6a  |.Signature..1(Lj|
00000210  61 76 61 2f 69 6f 2f 46  69 6c 65 3b 4c 6a 61 76  |ava/io/File;Ljav|
00000220  61 2f 75 74 69 6c 2f 4c  69 73 74 3c 4c 6a 61 76  |a/util/List<Ljav|
00000230  61 2f 69 6f 2f 46 69 6c  65 3b 3e 3b 29 56 01 00  |a/io/File;>;)V..|
00000240  04 6d 61 69 6e 01 00 16  28 5b 4c 6a 61 76 61 2f  |.main...([Ljava/|

```

Perhaps you need to apply a bit of thinking in order to get this output, though. Hint: gedit won't work.

---

### Post by Ramses de Norre on 2007-01-18
And that bit of thinking involves using a hex editor probably..
My point was that a normal human being doesn't take hours to decode such a thing, that's something we designed computers for.

---

### Post by Wybiral on 2007-01-18
I've spent the past few weeks looking at elf executables like this...

But, it isn't practical, especially not for java (is java ever practical? just kidding... Don't linch me)

Hex editors are useful when you are trying to understand the executable format, or when you need to manually optimize something (because contrary to popular belief, compilers aren't perfect, they are good... But you wouldn't imagine some of the dump stuff I've seen even the better C++ compilers do)

But... I've messed with decompilers, not for java, for C, and they rarely ever produce anything more intelligible than reading the hex values would be (unless you absolutely don't understand assembly at all)

I'm really interested how java bytecode is arranged... Does anyone have any links to a java bytecode outline or specifications that might enlighten me to how it works?

---

### Post by Ragazzo on 2007-01-18
Jad is what I've used too but of course it doesn't always produce code that can be recompiled. For something better than a hex editor, [http://cs.ioc.ee/~ando/jbe/](http://cs.ioc.ee/~ando/jbe/) looks promising.

---

### Post by phossal on 2007-01-18
You dopes. JAD, which is a *modest* decompiler at best, reproduces (Java) source from bytecode *with comments*. 

I've used a HEX editor before. And I've disassembled binaries before. I've reversed a medium-popular file format originated by a program written with Borland C++. 

This isn't the same thing. This is *much easier*. It doesn't require a hex editor, disassembler, etc. This is *bytecode*. This is *Java*. While it's still virtually impossible to decompile a binary produced by the *real* languages (at best they're *disassembled*), one has been able to decompile a Java program since the late '90's.

I just assumed there was a *better* alternative than Jad, which I think stalled out in the early part of this decade.

---

### Post by phossal on 2007-01-18
Ragazzo, amo-ej1, thanks.

---


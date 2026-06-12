---
title: "How do I delete lines from a mac file?"
date: 2014-06-30
forum: New to Ubuntu
---

### Post by Louise_Avon on 2014-06-30
There are a few lines I want to remove from a mac program. Can I do this in Ubuntu Terminal?

---

### Post by steeldriver on 2014-06-30
What kind of file / program? if it's plain text it should be no problem (although you may need to be careful about line termination characters, depending on what you use to do the editing)

---

### Post by Louise_Avon on 2014-06-30
The program is a photo editing demo  (.dmg file). I don't know what I could use to do the editing. I have seen the Directories on a File Activity app on my mac. If I delete those lines..whilst I am using the File Activity app it just deletes the information..not the actual lines in the file. I am not sure how to remove them or to get at them. I was wondering if Linux terminal or a app like Acetone iso could do the job or something similar?

---

### Post by Louise_Avon on 2014-06-30
[TABLE]
[TR]
[TD="class: votecell"]
           

              [/TD]
              [TD="class: postcell"]                [SIZE=3]Below is what I have typed into the Linux Terminal:
[/SIZE]
[SIZE=3]  [/SIZE][SIZE=3]parallels@LouiseAvon:~$ cd Desktop parallels@LouiseAvon:~/Desktop$ sed '1d' Lightroom4.dmg[/SIZE]

  
[SIZE=3]Next is the terminal result:[/SIZE] 

..s]G&#65533;&#1097;&#65533;2&#65533;&#65533;^             &#65533;&#65533;G&#65533;&#65533;&#10816;Gb&#65533;[<&#65533;&#65533;&#65533; &#65533;&#65533;!&#65533;[&#65533;{]&#65533;&#65533;0&#65533;&#65533;c6B&#65533;X&#65533;yl&#2045;&#65533;&#65533;~~&#725;[>}&#65533;g&#65533;YQ&#65533;&#65533;&#65533;&#65533;&#65533;=f&#65533;&#65533;&#65533;NNN&#65533;-&#65533;T&#65533;k&#65533;&#65533;&#65533;=&#65533;7n&#65533;'c&#65533;g&#65533;4\&#728;&#65533;&#65533;&#65533;%G&#65533;f&#990;&#65533;K&#65533;&#65533;T&#65533;l(K&#65533;;&#65533;&#65533;&#65533;/'6l&#65533;,^&#65533;d&#65533;&#65533;73\b7/&#65533;&#65533;&#260;&#65533;:&#65533;&#65533;&#65533;ch&#65533;&#910;k&#65533;2&#65533;&#65533;9Eo&#65533;&#65533;RV&#65533;&#65533;                                                               ,^&#65533;r;&#65533;l&#65533;&#65533;gfK&#65533;5&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;9&#1369;H&#65533;?kn&#65533;s&#65533;&#65533;V&#65533;}&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;r&#65533;&#65533;&#65533;G&#65533;&#65533;&#65533; &#17555;a&#65533;K                                            B&#65533;9&#65533;&#65533;8#&#65533;&#65533;Ug&#65533;&#65533;&#867;&#65533;1                                                                 E&#65533;D&-&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;h6&#65533;N)#F&#65533;y0&#65533;x&#65533;W/^&#65533;W&#65533;&#65533;K&&#65533;^&#65533;o7&#65533;&#715;&#65533;KE&#65533;  &#65533;&#65533;&&#65533;&#65533;r&#65533;&#65533;Z&#65533;&#65533;&#65533;8&#65533;&#65533;&#65533;&#65533;o&#65533;bs98&#65533;&#65533;&#65533;&#65533;V&#65533;g&#65533;&#65533;&#65533;o&#65533;&#65533;&#65533;&#65533;~$g&#65533;P,&#677;&#602;!&#65533;&#65533;&#65533;#&#65533;1&#65533;m&#65533;&#65533;&#65533;)xGaL&#65533;&#274;7r5&#65533;&#65533;4=C&#65533;&#65533;0&#65533;&#65533;9&#65533;&#65533;&#65533;elN&#1399;&#65533;:JK+~®&#65533;&#65533;&#65533;&#65533;Ku&#65533;~&#65533;B&#65533;_Z^~48&#65533;&#65533;PtZ#c&#65533;B&#65533;&#65533;&#65533;}r            *?&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;2^^&#65533;5Y^&#65533;&#65533;~&#65533; &#65533;f&#65533;&#65533;k /&#65533;&#65533;+&#65533;F'&#65533;&#65533;&#65533;8&#514;~&#65533;&#65533;is&#65533;}&#65533;&#65533;[&#65533;'&#65533;&#65533;&#926;T&#65533;ZWY$<i&#65533;S&#65533;&#65533;>&#65533;hh&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;I&#65533;&#807;&#65533;&#65533;9zko&#65533;ot&#65533;&#65533;&#1814;s$HIoM%&#65533;"&#65533;&#65533;&#65533;&#65533;4&#1780;&#65533;c       <F&#65533;&#65533;          8&#65533;k&#65533;&#65533;ž&#65533;&#1716;&#65533;&#65533;                        &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;eS&#65533;J&#65533;Y&#65533;&#65533;&#65533;Eu/&#65533;&#65533;[&#65533;&#65533;Z<i&#65533;&#65533;&#48971;&#65533;F74>IS]&#65533;&#65533;&#65533;YU<c&#65533;&#65533;]}&#65533;B&#65533;&#65533;&#410;&#65533;&#65533;&#65533;&#65533;&#65533;e&#65533;[&#65533;t&#65533;&#65533;&#65533;s3&#65533;&#65533;{<&#65533;$&#65533;&#65533;&#65533;9&#65533;&#65533;?&#65533;r&#65533;#g8f&#65533;R&#65533;&#65533;&#65533;&#65533;)p&#65533;&#65533;t&#65533;B`c9W&#65533;7&#65533;&#808;&#307;&#65533;&#65533;0&#65533;&#65533;&#65533;=&#65533;&#65533;SR                                                                                 7&#65533;&#65533;3&#65533;&#65533;&#65533;6&#65533;k&#65533;&#1150;&#65533;&#65533;&#65533;f&#65533;;&#65533;&#65533;0=&#65533;C8&#65533;&#65533;&#65533;xB&#65533;x&#65533;&#388;&#65533;&#65533;&#65533;kv&#65533;&#65533;&#1259;$&#65533;&#6795;&#65533;&#65533;oo\&#65533;q&#65533;&#65533;&#65533;M}bt'SJ \K&#65533;nbbrab&#65533;TeVzd&#15882;&#397;/s&#65533;P&#65533;&#65533;&#65533;&#65533;&#65533;r&#65533;&#65533;&#65533;&#65533;&#65533;EC&#65533;|&#65533;&#65533;L&#65533;b&#65533;&#65533;&#65533;&#65533;&#65533;Y&#65533;&#65533;&#65533;&#65533;&#1515;D%&#65533;&#65533;&#65533;M&#65533;&#65533;                                                            &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;w&#60570;&#65533;&#65533;<&#65533;&#65533;&#65533;&#65533;&#65533;2&#65533;&#65533;#&#65533;+&#65533;&#65533;&#65533;&#65533;[&#65533;i&#708;Pf\&#65533;&#65533;p(&#65533;"&#65533;&#65533;r&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;=&#65533;&#65533;&#65533;#&&#65533;&#65533;&#65533;7ww&#65533;,&#65533;0&#65533;<&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;y&#65533;&#65533;&#65533;&#65533;&#65533;Po ^Cparallels@LouiseAvon:~/Desktop$  

  
[SIZE=3]Its actually moving rapidly. I just want to remove line 1 from my mac  file. What I am doing wrong? Is the "sed" command the right command?  The website I obtained this info states its also a Unix command. Is this  true?[/SIZE]

      

[/TD]
[/TR]
[/TABLE]

---

### Post by steeldriver on 2014-06-30
It looks like the correct command to delete the first line from a line-based file - however if I understand correctly, a .dmg file is a *compressed disk image* which is essentially just binary data. The strange characters that you are seeing in the terminal are a result of trying to convert that binary data into printable output.

You will likely need to mount the image as a loop filesystem (possibly after decompressing it) and then find the particular file that you want to modify and apply the sed command to that. Depending on the underlying filesystem (hfs? hfs+?) you may need additional steps to make the filesystem writeable.

---

### Post by Louise_Avon on 2014-06-30
So do you think it would be, in all easier for me to use my Mac Unix Terminal instead of Linux?

---

### Post by buzzingrobot on 2014-06-30
Sed's a traditional Unix command. If memory serves, a .dmg file is a specific compressed archive format used in OS X. 

Both Ubuntu's and the OS X terminal use Bash, and sed is available on both, so choice of system probably doesn't matter much.

make a copy of the file for experimentation.  I think something like this might work:```


sed -i "s/StringToReplace/ReplacementString/g" The.dmg


```

That wiil replace every instance of the old string in the file with the new string. It changes the file in place; it doesn't write out a new edited copy.   Sed doesn't know about the compression, so it won't see any compressed versions of the string, if they exist.

This assumes sed can read and make sense of the dmg file.... I dunno about that.

---

### Post by QIII on 2014-06-30
Closed for Staff review.

---


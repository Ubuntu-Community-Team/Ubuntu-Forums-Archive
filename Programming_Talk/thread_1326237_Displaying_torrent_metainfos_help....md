---
title: "Displaying torrent metainfos help..."
date: 2009-11-14
forum: Programming Talk
---

### Post by meson2439 on 2009-11-14
How to read a *.torrent meta infos? I tried gedit and it cannot recognize the encodings and even nano give something incomprehensible. Afterwards, I made a simple C code to read the first 1000 characters and it works only for the first few characters. Here's the output:
```

d8:announce43:http://tracker.datorrents.com:6969/announce7:comment19:http://aerosubs.net10:created by13:uTorrent/180013:creation datei1224165828e8:encoding5:UTF-84:infod6:lengthi173765965e4:name38:Toradora_-_03[h264][848x480][Aero].mkv12:piece lengthi262144e6:pieces13260:C&#65533;Q&#65533;&#65533;&#65533;&#65533;W|&#65533;&#65533;&#65533;&#1323;&#65533;&#65533;&#1592;{pkn@od&#65533;&#65533;W&#65533;a&#65533;&#65533;B&#65533;&#65533;&#65533;fb|&#65533;&#65533;&#65533;&#65533;&#65533;A&#65533;*&#65533;&#65533;0:&#65533;&#65533;&#65533;C&#65533;9	}&#65533;+&#65533;}D&#65533;&#65533;C&#65533;&#65533;u?&#65533;&#65533;&#65533;&#2023;p&#65533;&#65533;>&#65533;!&#65533;&#65533;&#65533;&#65533;f9H&#65533;7&#65533;Q8H&#65533;&#65533;
                                       &#65533;&#65533;c&#65533;&#65533;EU&#65533;&#65533;bx&#65533;&#65533;;&#65533;&#1675;&#65533;&#65533;~%u@)&#65533; &#65533;b&#65533;k';H&#65533;&#65533;&#65533;x&#65533;&#65533;&#65533;v&#65533;&#65533;v&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;I&#65533;&#65533;_&#65533;|N(&#65533;&#65533;&#65533;&#65533;T{4&#65533;&#65533;&#65533;TH8&#65533;M&#65533;&#65533;A`&#65533;&#65533;{K&#65533;&&#65533;y&#65533;&#65533;&#65533;52C!&#65533;k&#65533;K&#65533;&#65533;&#65533;	&#65533;&#65533;&#65533;&#65533;&#65533;&v[&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
                                                         &#65533;&#65533;&#65533;c·ÀKå;³¬A<5ÄÝò7&#65533;ûÿ&#9226;&#9229;©&#9228;Ùì[&#8222;³Ñ£ùäÑÔç&#65533;&#376;\À&#65533;&#9500;à&#9147;Å!ï@(&#338;¡ï&#9148;ì¼Ç&#65533;Êç¹ôôºM¾&#9484;Ë&#8805;&#8225;&#9500;&#8230;]&#339;«Å¦0W&#8220;&#382;¼Û«
                                              G&#8220;] ¨ë&#9474;¢&#8364;!å&#9225;æGÞ«	ñ&#8226;,ý®èÚ?ì&#8221;&#8216;&#8805;çÒáí-	NWð&#339;¼&#8230;·DÕ&#338;Ô&#65533;º&#960;&#9148;

Ë¯ÏÉ®þ&#9474;TLÝ6&#382;È0A&#376;PYT´P&#65533;&#65533;.F»êöMá&#8216;ø.&#8224;9îÔ&#8217;ÁT&#9146;$=KBHÕ?ôá_&#8805;&#65533;E0¸\MLAÒ&#9472;±ì&#710;&#338;&#9226;&#9484;²&#382;õQ&#8221;&#339;5øú&#8240;ÊËI&#9149;û°¦ù4&#8249;&#9149;&#8217;8&#402;&#9500;&#9488;
                                                                                                        3á®ðñÎÈ&#65533;7·Qù	©*&#9474;&#338;úÍ·&#8230;¿ôÝ÷&#65533;&#65533;
+µ&#65533;¸8F&#8225;J>&#8211;á4&#8482;Hµ&#8226;KÇ. %%&#8220;L

```

And the codes used to read it is this one.

```

#include <stdio.h>

int main(int argc, char *argv[])
{
	int k;
	char data;
	FILE *torrentfiles;
	torrentfiles=fopen(argv[1],"r");
	//printf("%d\n",argc);
	for (k=0;k<1000;k++)
	{
		fscanf(torrentfiles,"%c",&data);
		printf("%c",data);
	}
	printf("\n");
	fclose(torrentfiles);
		
	return 0;
}
```

I know that the metainfos are bencoded, but my objective is only to display everything, so how should I do that? Thanks for any advice.

---

### Post by stylishpants on 2009-11-16
Perhaps this utility will provide all you need.
It's in the package libbtutil-utils.

```

bob@cob:~$ bt_showmetainfo Nobody_Knows__[Japan_2004].3320213.TPB.torrent
bt_showmetainfo 0.0.19 - decode BitTorrent metainfo files

metainfo file.: Nobody_Knows__[Japan_2004].3320213.TPB.torrent
info hash.....: 010192a1287a027a6e47c18ae9893d19895abdfa
directory name: [2004] Nobody Knows
files.........:
   tlf-nk.cd1.avi (733976576)
   tlf-nk.cd1.idx (128112)
   tlf-nk.cd1.rar (1162981)
   tlf-nk.cd2.avi (734343168)
   tlf-nk.cd2.idx (47356)
   tlf-nk.cd2.rar (422366)
archive size..: 1470080559 (1401 * 1048576 + 1025583)
announce url..: http://tracker.thepirtebay.org/announce

```

Otherwise, you should refer to BEP-003 and its extensions for information on writing code to unpack a torrent file.  See the links at the end of the wikipedia article:
[http://en.wikipedia.org/wiki/Torrent_file](http://en.wikipedia.org/wiki/Torrent_file)

---

### Post by meson2439 on 2009-11-17
Thanks for the info... I will try looking at it. I'm still wondering why I couldn't read the file since it is supposed to be utf8 and everything. But if you see the output, I already found the file name, amount of pieces, size, announce and most of the stuff given by the utility. The rest of it might be the hash information. Maybe I should look into reading hash instead.

---

### Post by stylishpants on 2009-11-18
You are misunderstanding the format.  A torrent file is not supposed to be UTF-8.  Strings within the file are supposed to be UTF-8 encoded, but there is a lot of other stuff in the file besides strings.

Because the file is bencoded, it is guaranteed to be ascii, but not all ascii characters are printable, so many of them will still show up as gibberish in a text editor.  This is what you're seeing.

Things seem to go nuts after the first few hundred bytes of this file because you run into the "pieces" field.  It happens here, right after the "piece length" field is shown:

```

piece lengthi262144e6:pieces13260:C&#65533;Q&#65533;&#65533;&#65533;&#65533;W
```

Remember that the file is laid out as a dictionary, so it is just a bunch of key-value pairs being defined.

In the snippet above, we see the "piece length" field named, and then it's value (i262144e6, which means the integer value 262144e6.)
Next is the "pieces" field, which is a byte string type.  After the "pieces" field name, we see 13260, which is the field length, followed by a series of ascii characters. 

The pieces field is explained as follows in the Wikipedia article on the torrent file format:```

pieces - the concatenation of the SHA-1's of each piece. As SHA-1 returns a 160-bit hash, 
pieces will be a string whose length is a multiple of 160-bits.
```

The main point is, that's binary data, so it's not meaningful to print it in a terminal, so that's why the bt_showmetainfo doesn't show it.  

So what you should do depends on what you want to do with the SHA-1 hashes.  They're just not very human-readable data.

---

### Post by meson2439 on 2009-11-19
lol.. no wonder. I will study hashes instead. Thanks for the help.

---


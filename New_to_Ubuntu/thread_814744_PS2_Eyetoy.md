---
title: "PS2 Eyetoy"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by ImThatNerd on 2008-06-01
I want to set up my PS2 Eyetoy to work on Ubuntu. I heard it works, but cannot find any directions that work. I heard it needs some drivers and stuff for it to work, but when I try it doesn't work. Any help would be great!

Thanks

---

### Post by quelx on 2008-06-01
[http://alpha.dyndns.org/ov511/](http://alpha.dyndns.org/ov511/)

from: [http://ubuntuforums.org/showthread.php?t=189978](http://ubuntuforums.org/showthread.php?t=189978)

---

### Post by ImThatNerd on 2008-06-01
> **quelx said:**
> [http://alpha.dyndns.org/ov511/](http://alpha.dyndns.org/ov511/)

from: [http://ubuntuforums.org/showthread.php?t=189978](http://ubuntuforums.org/showthread.php?t=189978)

Yeah I saw that post. But not really sure what to do with it once I downloaded it.

---

### Post by quelx on 2008-06-01
Which step are you stuck on?

[http://alpha.dyndns.org/ov511/install.html](http://alpha.dyndns.org/ov511/install.html)

---

### Post by ImThatNerd on 2008-06-01
Okay I found the insallation page here:

[http://alpha.dyndns.org/ov511/install.html](http://alpha.dyndns.org/ov511/install.html)

So I downloaded the most current version of the driver and extracted it to my home folder. I then navigated to the folder and did 'make' got tons of errors so I did make install, then it made me select kernal version so I did make install-2.5. I got all these errors and it said if you get errors add that line of text to make install so I added it near top and saved it and ran it again and all same errors. Here were the errors

```
ov511.c:4957: warning: statement with no effect
ov511.c:4958: error: dereferencing pointer to incomplete type
ov511.c:4958: error: request for member &#8216;minwidth&#8217; in something not a structure or union
ov511.c:4958: warning: statement with no effect
ov511.c:4959: error: dereferencing pointer to incomplete type
ov511.c:4959: error: request for member &#8216;minheight&#8217; in something not a structure or union
ov511.c:4959: warning: statement with no effect
ov511.c:4963: error: &#8216;VIDIOCGCHAN&#8217; undeclared (first use in this function)
ov511.c:4969: error: dereferencing pointer to incomplete type
ov511.c:4969: error: request for member &#8216;channel&#8217; in something not a structure or union
ov511.c:4970: error: dereferencing pointer to incomplete type
ov511.c:4970: error: request for member &#8216;channel&#8217; in something not a structure or union
ov511.c:4970: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 3 has type &#8216;struct symbolic_list *&#8217;
ov511.c:4974: error: dereferencing pointer to incomplete type
ov511.c:4974: error: request for member &#8216;norm&#8217; in something not a structure or union
ov511.c:4974: warning: statement with no effect
ov511.c:4975: error: dereferencing pointer to incomplete type
ov511.c:4975: error: request for member &#8216;type&#8217; in something not a structure or union
ov511.c:4975: error: &#8216;VIDEO_TYPE_CAMERA&#8217; undeclared (first use in this function)
ov511.c:4975: warning: statement with no effect
ov511.c:4976: error: dereferencing pointer to incomplete type
ov511.c:4976: error: request for member &#8216;flags&#8217; in something not a structure or union
ov511.c:4976: warning: statement with no effect
ov511.c:4978: error: dereferencing pointer to incomplete type
ov511.c:4978: error: request for member &#8216;tuners&#8217; in something not a structure or union
ov511.c:4978: warning: statement with no effect
ov511.c:4979: error: dereferencing pointer to incomplete type
ov511.c:4979: error: request for member &#8216;channel&#8217; in something not a structure or union
ov511.c:4979: error: dereferencing pointer to incomplete type
ov511.c:4979: error: request for member &#8216;name&#8217; in something not a structure or union
ov511.c:4979: warning: passing argument 2 of &#8216;decoder_get_input_name&#8217; makes integer from pointer without a cast
ov511.c:4979: warning: passing argument 3 of &#8216;decoder_get_input_name&#8217; from incompatible pointer type
ov511.c:4983: error: &#8216;VIDIOCSCHAN&#8217; undeclared (first use in this function)
ov511.c:4992: error: dereferencing pointer to incomplete type
ov511.c:4992: error: request for member &#8216;channel&#8217; in something not a structure or union
ov511.c:4998: error: dereferencing pointer to incomplete type
ov511.c:4998: error: request for member &#8216;norm&#8217; in something not a structure or union
ov511.c:4998: error: &#8216;VIDEO_MODE_PAL&#8217; undeclared (first use in this function)
ov511.c:4999: error: dereferencing pointer to incomplete type
ov511.c:4999: error: request for member &#8216;norm&#8217; in something not a structure or union
ov511.c:4999: error: &#8216;VIDEO_MODE_NTSC&#8217; undeclared (first use in this function)
ov511.c:5000: error: dereferencing pointer to incomplete type
ov511.c:5000: error: request for member &#8216;norm&#8217; in something not a structure or union
ov511.c:5000: error: &#8216;VIDEO_MODE_SECAM&#8217; undeclared (first use in this function)
ov511.c:5001: error: dereferencing pointer to incomplete type
ov511.c:5001: error: request for member &#8216;norm&#8217; in something not a structure or union
ov511.c:5001: error: &#8216;VIDEO_MODE_AUTO&#8217; undeclared (first use in this function)
ov511.c:5002: error: dereferencing pointer to incomplete type
ov511.c:5002: error: request for member &#8216;norm&#8217; in something not a structure or union
ov511.c:5002: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 3 has type &#8216;struct symbolic_list *&#8217;
ov511.c:5006: error: dereferencing pointer to incomplete type
ov511.c:5006: error: request for member &#8216;channel&#8217; in something not a structure or union
ov511.c:5007: error: dereferencing pointer to incomplete type
ov511.c:5007: error: request for member &#8216;channel&#8217; in something not a structure or union
ov511.c:5007: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 3 has type &#8216;struct symbolic_list *&#8217;
ov511.c:5011: error: dereferencing pointer to incomplete type
ov511.c:5011: error: request for member &#8216;channel&#8217; in something not a structure or union
ov511.c:5011: warning: passing argument 2 of &#8216;decoder_set_input&#8217; makes integer from pointer without a cast
ov511.c:5015: error: dereferencing pointer to incomplete type
ov511.c:5015: error: request for member &#8216;norm&#8217; in something not a structure or union
ov511.c:5015: warning: passing argument 2 of &#8216;decoder_set_norm&#8217; makes integer from pointer without a cast
ov511.c:5021: error: &#8216;VIDIOCGPICT&#8217; undeclared (first use in this function)
ov511.c:5027: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_picture&#8217; 
ov511.c:5028: warning: passing argument 2 of &#8216;sensor_get_picture&#8217; from incompatible pointer type
ov511.c:5032: error: dereferencing pointer to incomplete type
ov511.c:5032: error: request for member &#8216;depth&#8217; in something not a structure or union
ov511.c:5032: warning: statement with no effect
ov511.c:5033: error: dereferencing pointer to incomplete type
ov511.c:5033: error: request for member &#8216;palette&#8217; in something not a structure or union
ov511.c:5033: warning: statement with no effect
ov511.c:5037: error: &#8216;VIDIOCSPICT&#8217; undeclared (first use in this function)
ov511.c:5044: error: dereferencing pointer to incomplete type
ov511.c:5044: error: request for member &#8216;palette&#8217; in something not a structure or union
ov511.c:5044: warning: passing argument 1 of &#8216;get_depth&#8217; makes integer from pointer without a cast
ov511.c:5047: warning: passing argument 2 of &#8216;sensor_set_picture&#8217; from incompatible pointer type
ov511.c:5050: error: dereferencing pointer to incomplete type
ov511.c:5050: error: request for member &#8216;palette&#8217; in something not a structure or union
ov511.c:5050: warning: comparison between pointer and integer
ov511.c:5051: error: dereferencing pointer to incomplete type
ov511.c:5051: error: request for member &#8216;palette&#8217; in something not a structure or union
ov511.c:5051: warning: passing argument 2 of &#8216;symbolic&#8217; makes integer from pointer without a cast
ov511.c:5057: error: dereferencing pointer to incomplete type
ov511.c:5057: error: request for member &#8216;palette&#8217; in something not a structure or union
ov511.c:5057: warning: comparison between pointer and integer
ov511.c:5065: error: dereferencing pointer to incomplete type
ov511.c:5065: error: request for member &#8216;palette&#8217; in something not a structure or union
ov511.c:5065: warning: passing argument 4 of &#8216;mode_init_regs&#8217; makes integer from pointer without a cast
ov511.c:5068: error: dereferencing pointer to incomplete type
ov511.c:5068: error: request for member &#8216;depth&#8217; in something not a structure or union
ov511.c:5068: error: dereferencing pointer to incomplete type
ov511.c:5068: error: request for member &#8216;palette&#8217; in something not a structure or union
ov511.c:5068: warning: passing argument 2 of &#8216;symbolic&#8217; makes integer from pointer without a cast
ov511.c:5068: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 5 has type &#8216;struct symbolic_list *&#8217;
ov511.c:5072: error: dereferencing pointer to incomplete type
ov511.c:5072: error: request for member &#8216;depth&#8217; in something not a structure or union
ov511.c:5072: warning: assignment makes integer from pointer without a cast
ov511.c:5073: error: dereferencing pointer to incomplete type
ov511.c:5073: error: request for member &#8216;palette&#8217; in something not a structure or union
ov511.c:5073: warning: assignment makes integer from pointer without a cast
ov511.c:5078: error: &#8216;VIDIOCGCAPTURE&#8217; undeclared (first use in this function)
ov511.c:5087: error: &#8216;VIDIOCSCAPTURE&#8217; undeclared (first use in this function)
ov511.c:5093: error: dereferencing pointer to incomplete type
ov511.c:5093: error: request for member &#8216;flags&#8217; in something not a structure or union
ov511.c:5095: error: dereferencing pointer to incomplete type
ov511.c:5095: error: request for member &#8216;decimation&#8217; in something not a structure or union
ov511.c:5098: error: dereferencing pointer to incomplete type
ov511.c:5098: error: request for member &#8216;x&#8217; in something not a structure or union
ov511.c:5098: warning: statement with no effect
ov511.c:5099: error: dereferencing pointer to incomplete type
ov511.c:5099: error: request for member &#8216;y&#8217; in something not a structure or union
ov511.c:5099: warning: statement with no effect
ov511.c:5100: error: dereferencing pointer to incomplete type
ov511.c:5100: error: request for member &#8216;y&#8217; in something not a structure or union
ov511.c:5100: warning: statement with no effect
ov511.c:5102: error: dereferencing pointer to incomplete type
ov511.c:5102: error: request for member &#8216;width&#8217; in something not a structure or union
ov511.c:5103: error: dereferencing pointer to incomplete type
ov511.c:5103: error: request for member &#8216;width&#8217; in something not a structure or union
ov511.c:5103: warning: statement with no effect
ov511.c:5105: error: dereferencing pointer to incomplete type
ov511.c:5105: error: request for member &#8216;height&#8217; in something not a structure or union
ov511.c:5105: warning: statement with no effect
ov511.c:5106: error: dereferencing pointer to incomplete type
ov511.c:5106: error: request for member &#8216;height&#8217; in something not a structure or union
ov511.c:5106: warning: statement with no effect
ov511.c:5107: error: dereferencing pointer to incomplete type
ov511.c:5107: error: request for member &#8216;height&#8217; in something not a structure or union
ov511.c:5108: error: dereferencing pointer to incomplete type
ov511.c:5108: error: request for member &#8216;height&#8217; in something not a structure or union
ov511.c:5108: warning: statement with no effect
ov511.c:5110: error: dereferencing pointer to incomplete type
ov511.c:5110: error: request for member &#8216;x&#8217; in something not a structure or union
ov511.c:5110: warning: assignment makes integer from pointer without a cast
ov511.c:5111: error: dereferencing pointer to incomplete type
ov511.c:5111: error: request for member &#8216;y&#8217; in something not a structure or union
ov511.c:5111: warning: assignment makes integer from pointer without a cast
ov511.c:5112: error: dereferencing pointer to incomplete type
ov511.c:5112: error: request for member &#8216;width&#8217; in something not a structure or union
ov511.c:5112: warning: assignment makes integer from pointer without a cast
ov511.c:5113: error: dereferencing pointer to incomplete type
ov511.c:5113: error: request for member &#8216;height&#8217; in something not a structure or union
ov511.c:5113: warning: assignment makes integer from pointer without a cast
ov511.c:5117: error: &#8216;VIDIOCSWIN&#8217; undeclared (first use in this function)
ov511.c:5122: error: dereferencing pointer to incomplete type
ov511.c:5122: error: request for member &#8216;width&#8217; in something not a structure or union
ov511.c:5122: error: dereferencing pointer to incomplete type
ov511.c:5122: error: request for member &#8216;height&#8217; in something not a structure or union
ov511.c:5122: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 5 has type &#8216;struct symbolic_list *&#8217;
ov511.c:5122: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 6 has type &#8216;struct symbolic_list *&#8217;
ov511.c:5139: error: dereferencing pointer to incomplete type
ov511.c:5139: error: request for member &#8216;width&#8217; in something not a structure or union
ov511.c:5139: error: dereferencing pointer to incomplete type
ov511.c:5139: error: request for member &#8216;height&#8217; in something not a structure or union
ov511.c:5140: warning: passing argument 2 of &#8216;mode_init_regs&#8217; makes integer from pointer without a cast
ov511.c:5140: warning: passing argument 3 of &#8216;mode_init_regs&#8217; makes integer from pointer without a cast
ov511.c:5145: error: dereferencing pointer to incomplete type
ov511.c:5145: error: request for member &#8216;width&#8217; in something not a structure or union
ov511.c:5145: warning: assignment makes integer from pointer without a cast
ov511.c:5146: error: dereferencing pointer to incomplete type
ov511.c:5146: error: request for member &#8216;height&#8217; in something not a structure or union
ov511.c:5146: warning: assignment makes integer from pointer without a cast
ov511.c:5151: error: &#8216;VIDIOCGWIN&#8217; undeclared (first use in this function)
ov511.c:5155: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_window&#8217; 
ov511.c:5156: error: dereferencing pointer to incomplete type
ov511.c:5156: error: request for member &#8216;x&#8217; in something not a structure or union
ov511.c:5156: warning: statement with no effect
ov511.c:5157: error: dereferencing pointer to incomplete type
ov511.c:5157: error: request for member &#8216;y&#8217; in something not a structure or union
ov511.c:5157: warning: statement with no effect
ov511.c:5158: error: dereferencing pointer to incomplete type
ov511.c:5158: error: request for member &#8216;width&#8217; in something not a structure or union
ov511.c:5158: warning: statement with no effect
ov511.c:5159: error: dereferencing pointer to incomplete type
ov511.c:5159: error: request for member &#8216;height&#8217; in something not a structure or union
ov511.c:5159: warning: statement with no effect
ov511.c:5160: error: dereferencing pointer to incomplete type
ov511.c:5160: error: request for member &#8216;flags&#8217; in something not a structure or union
ov511.c:5160: warning: statement with no effect
ov511.c:5162: error: dereferencing pointer to incomplete type
ov511.c:5162: error: request for member &#8216;width&#8217; in something not a structure or union
ov511.c:5162: error: dereferencing pointer to incomplete type
ov511.c:5162: error: request for member &#8216;height&#8217; in something not a structure or union
ov511.c:5162: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 5 has type &#8216;struct symbolic_list *&#8217;
ov511.c:5162: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 6 has type &#8216;struct symbolic_list *&#8217;
ov511.c:5166: error: &#8216;VIDIOCGMBUF&#8217; undeclared (first use in this function)
ov511.c:5173: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_mbuf&#8217; 
ov511.c:5174: error: dereferencing pointer to incomplete type
ov511.c:5174: error: request for member &#8216;size&#8217; in something not a structure or union
ov511.c:5175: warning: statement with no effect
ov511.c:5176: error: dereferencing pointer to incomplete type
ov511.c:5176: error: request for member &#8216;frames&#8217; in something not a structure or union
ov511.c:5176: warning: statement with no effect
ov511.c:5178: error: dereferencing pointer to incomplete type
ov511.c:5178: error: request for member &#8216;offsets&#8217; in something not a structure or union
ov511.c:5178: error: incompatible types in assignment
ov511.c:5178: warning: statement with no effect
ov511.c:5180: error: dereferencing pointer to incomplete type
ov511.c:5180: error: request for member &#8216;offsets&#8217; in something not a structure or union
ov511.c:5180: error: dereferencing pointer to incomplete type
ov511.c:5180: error: request for member &#8216;offsets&#8217; in something not a structure or union
ov511.c:5181: error: invalid operands to binary +
ov511.c:5181: error: incompatible types in assignment
ov511.c:5181: warning: statement with no effect
ov511.c:5186: error: &#8216;VIDIOCMCAPTURE&#8217; undeclared (first use in this function)
ov511.c:5190: error: dereferencing pointer to incomplete type
ov511.c:5190: error: request for member &#8216;frame&#8217; in something not a structure or union
ov511.c:5190: warning: initialization makes integer from pointer without a cast
ov511.c:5192: error: dereferencing pointer to incomplete type
ov511.c:5192: error: request for member &#8216;width&#8217; in something not a structure or union
ov511.c:5192: error: dereferencing pointer to incomplete type
ov511.c:5192: error: request for member &#8216;height&#8217; in something not a structure or union
ov511.c:5192: error: dereferencing pointer to incomplete type
ov511.c:5192: error: request for member &#8216;format&#8217; in something not a structure or union
ov511.c:5192: warning: passing argument 2 of &#8216;symbolic&#8217; makes integer from pointer without a cast
ov511.c:5192: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 6 has type &#8216;struct symbolic_list *&#8217;
ov511.c:5192: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 7 has type &#8216;struct symbolic_list *&#8217;
ov511.c:5195: error: dereferencing pointer to incomplete type
ov511.c:5195: error: request for member &#8216;format&#8217; in something not a structure or union
ov511.c:5195: warning: passing argument 1 of &#8216;get_depth&#8217; makes integer from pointer without a cast
ov511.c:5197: error: dereferencing pointer to incomplete type
ov511.c:5197: error: request for member &#8216;format&#8217; in something not a structure or union
ov511.c:5197: warning: passing argument 2 of &#8216;symbolic&#8217; makes integer from pointer without a cast
ov511.c:5207: error: dereferencing pointer to incomplete type
ov511.c:5207: error: request for member &#8216;width&#8217; in something not a structure or union
ov511.c:5208: warning: comparison between pointer and integer
ov511.c:5208: error: dereferencing pointer to incomplete type
ov511.c:5208: error: request for member &#8216;height&#8217; in something not a structure or union
ov511.c:5208: warning: comparison between pointer and integer
ov511.c:5218: error: dereferencing pointer to incomplete type
ov511.c:5218: error: request for member &#8216;format&#8217; in something not a structure or union
ov511.c:5218: warning: comparison between pointer and integer
ov511.c:5219: error: dereferencing pointer to incomplete type
ov511.c:5219: error: request for member &#8216;format&#8217; in something not a structure or union
ov511.c:5219: warning: passing argument 2 of &#8216;symbolic&#8217; makes integer from pointer without a cast
ov511.c:5224: error: dereferencing pointer to incomplete type
ov511.c:5224: error: request for member &#8216;width&#8217; in something not a structure or union
ov511.c:5224: warning: comparison between pointer and integer
ov511.c:5225: error: dereferencing pointer to incomplete type
ov511.c:5225: error: request for member &#8216;height&#8217; in something not a structure or union
ov511.c:5225: warning: comparison between pointer and integer
ov511.c:5226: error: dereferencing pointer to incomplete type
ov511.c:5226: error: request for member &#8216;format&#8217; in something not a structure or union
ov511.c:5226: warning: comparison between pointer and integer
ov511.c:5235: error: dereferencing pointer to incomplete type
ov511.c:5235: error: request for member &#8216;width&#8217; in something not a structure or union
ov511.c:5235: error: dereferencing pointer to incomplete type
ov511.c:5235: error: request for member &#8216;height&#8217; in something not a structure or union
ov511.c:5236: error: dereferencing pointer to incomplete type
ov511.c:5236: error: request for member &#8216;format&#8217; in something not a structure or union
ov511.c:5236: warning: passing argument 2 of &#8216;mode_init_regs&#8217; makes integer from pointer without a cast
ov511.c:5236: warning: passing argument 3 of &#8216;mode_init_regs&#8217; makes integer from pointer without a cast
ov511.c:5236: warning: passing argument 4 of &#8216;mode_init_regs&#8217; makes integer from pointer without a cast
ov511.c:5243: error: dereferencing pointer to incomplete type
ov511.c:5243: error: request for member &#8216;width&#8217; in something not a structure or union
ov511.c:5243: warning: assignment makes integer from pointer without a cast
ov511.c:5244: error: dereferencing pointer to incomplete type
ov511.c:5244: error: request for member &#8216;height&#8217; in something not a structure or union
ov511.c:5244: warning: assignment makes integer from pointer without a cast
ov511.c:5245: error: dereferencing pointer to incomplete type
ov511.c:5245: error: request for member &#8216;format&#8217; in something not a structure or union
ov511.c:5245: warning: assignment makes integer from pointer without a cast
ov511.c:5257: error: &#8216;VIDIOCSYNC&#8217; undeclared (first use in this function)
ov511.c:5320: error: &#8216;VIDIOCGFBUF&#8217; undeclared (first use in this function)
ov511.c:5326: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_buffer&#8217; 
ov511.c:5330: error: &#8216;VIDIOCGUNIT&#8217; undeclared (first use in this function)
ov511.c:5336: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_unit&#8217; 
ov511.c:5338: error: dereferencing pointer to incomplete type
ov511.c:5338: error: request for member &#8216;video&#8217; in something not a structure or union
ov511.c:5338: error: request for member &#8216;minor&#8217; in something not a structure or union
ov511.c:5338: warning: statement with no effect
ov511.c:5339: error: dereferencing pointer to incomplete type
ov511.c:5339: error: request for member &#8216;vbi&#8217; in something not a structure or union
ov511.c:5339: error: &#8216;VIDEO_NO_UNIT&#8217; undeclared (first use in this function)
ov511.c:5339: warning: statement with no effect
ov511.c:5340: error: dereferencing pointer to incomplete type
ov511.c:5340: error: request for member &#8216;radio&#8217; in something not a structure or union
ov511.c:5340: warning: statement with no effect
ov511.c:5341: error: dereferencing pointer to incomplete type
ov511.c:5341: error: request for member &#8216;audio&#8217; in something not a structure or union
ov511.c:5341: warning: statement with no effect
ov511.c:5342: error: dereferencing pointer to incomplete type
ov511.c:5342: error: request for member &#8216;teletext&#8217; in something not a structure or union
ov511.c:5342: warning: statement with no effect
ov511.c:5346: error: &#8216;BASE_VIDIOCPRIVATE&#8217; undeclared (first use in this function)
ov511.c:5346: error: invalid operands to binary <<
ov511.c:5346: error: invalid operands to binary |
ov511.c:5346: error: invalid operands to binary |
ov511.c:5352: error: invalid operands to binary <<
ov511.c:5352: error: invalid operands to binary |
ov511.c:5352: error: invalid operands to binary |
ov511.c: In function &#8216;ov51x_v4l1_ioctl&#8217;:
ov511.c:5450: error: dereferencing pointer to incomplete type
ov511.c:5450: error: request for member &#8216;priv&#8217; in something not a structure or union
ov511.c:5450: warning: initialization from incompatible pointer type
ov511.c:5456: warning: implicit declaration of function &#8216;video_usercopy&#8217;
ov511.c: In function &#8216;ov51x_v4l1_read&#8217;:
ov511.c:5476: error: dereferencing pointer to incomplete type
ov511.c:5476: error: request for member &#8216;priv&#8217; in something not a structure or union
ov511.c:5476: warning: initialization from incompatible pointer type
ov511.c: In function &#8216;ov51x_v4l1_mmap&#8217;:
ov511.c:5644: error: dereferencing pointer to incomplete type
ov511.c:5644: error: request for member &#8216;priv&#8217; in something not a structure or union
ov511.c:5644: warning: initialization from incompatible pointer type
ov511.c:5664: warning: implicit declaration of function &#8216;remap_page_range&#8217;
ov511.c:5665: warning: left shift count >= width of type
ov511.c: At top level:
ov511.c:5705: warning: initialization from incompatible pointer type
ov511.c:5711: error: variable &#8216;vdev_template&#8217; has initializer but incomplete type
ov511.c:5712: error: unknown field &#8216;owner&#8217; specified in initializer
ov511.c:5712: warning: excess elements in struct initializer
ov511.c:5712: warning: (near initialization for &#8216;vdev_template&#8217;)
ov511.c:5713: error: unknown field &#8216;name&#8217; specified in initializer
ov511.c:5713: warning: excess elements in struct initializer
ov511.c:5713: warning: (near initialization for &#8216;vdev_template&#8217;)
ov511.c:5714: error: unknown field &#8216;type&#8217; specified in initializer
ov511.c:5714: warning: excess elements in struct initializer
ov511.c:5714: warning: (near initialization for &#8216;vdev_template&#8217;)
ov511.c:5715: error: unknown field &#8216;hardware&#8217; specified in initializer
ov511.c:5715: error: &#8216;VID_HARDWARE_OV511&#8217; undeclared here (not in a function)
ov511.c:5715: warning: excess elements in struct initializer
ov511.c:5715: warning: (near initialization for &#8216;vdev_template&#8217;)
ov511.c:5716: error: unknown field &#8216;fops&#8217; specified in initializer
ov511.c:5716: warning: excess elements in struct initializer
ov511.c:5716: warning: (near initialization for &#8216;vdev_template&#8217;)
ov511.c: In function &#8216;saa7111a_configure&#8217;:
ov511.c:6397: error: &#8216;VIDEO_MODE_AUTO&#8217; undeclared (first use in this function)
ov511.c:6397: warning: assignment makes integer from pointer without a cast
ov511.c: In function &#8216;ov518_configure&#8217;:
ov511.c:6677: warning: initialization from incompatible pointer type
ov511.c:6678: error: &#8216;struct usb_host_endpoint&#8217; has no member named &#8216;wMaxPacketSize&#8217;
ov511.c:6678: warning: initialization makes integer from pointer without a cast
ov511.c: In function &#8216;ov51x_probe&#8217;:
ov511.c:6782: warning: assignment from incompatible pointer type
ov511.c:6940: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_device&#8217; 
ov511.c:6940: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_device&#8217; 
ov511.c:6941: error: request for member &#8216;priv&#8217; in something not a structure or union
ov511.c:6941: warning: statement with no effect
ov511.c:6949: warning: implicit declaration of function &#8216;video_register_device&#8217;
ov511.c:6949: error: &#8216;VFL_TYPE_GRABBER&#8217; undeclared (first use in this function)
ov511.c:6967: error: request for member &#8216;minor&#8217; in something not a structure or union
ov511.c:6967: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 4 has type &#8216;struct symbolic_list *&#8217;
ov511.c:7017: error: invalid storage class for function &#8216;ov51x_disconnect&#8217;
ov511.c: In function &#8216;ov51x_disconnect&#8217;:
ov511.c:7045: warning: implicit declaration of function &#8216;video_unregister_device&#8217;
ov511.c: In function &#8216;ov51x_probe&#8217;:
ov511.c:7088: error: unknown field &#8216;owner&#8217; specified in initializer
ov511.c:7088: warning: initialization from incompatible pointer type
ov511.c:7096: error: initializer element is not constant
ov511.c:7096: error: (near initialization for &#8216;ov511_driver.disconnect&#8217;)
ov511.c: In function &#8216;ov511_register_decomp_module&#8217;:
ov511.c:7152: error: &#8216;MOD_INC_USE_COUNT&#8217; undeclared (first use in this function)
ov511.c:7152: warning: statement with no effect
ov511.c: In function &#8216;ov511_deregister_decomp_module&#8217;:
ov511.c:7179: error: &#8216;MOD_DEC_USE_COUNT&#8217; undeclared (first use in this function)
ov511.c:7179: warning: statement with no effect
ov511.c: In function &#8216;ov51x_probe&#8217;:
ov511.c:7186: error: invalid storage class for function &#8216;usb_ov511_init&#8217;
ov511.c:7208: error: invalid storage class for function &#8216;usb_ov511_exit&#8217;
ov511.c:7215: error: invalid storage class for function &#8216;__inittest&#8217;
ov511.c:7215: warning: &#8216;alias&#8217; attribute ignored
ov511.c:7216: error: invalid storage class for function &#8216;__exittest&#8217;
ov511.c:7216: warning: &#8216;alias&#8217; attribute ignored
ov511.c:7219: error: expected declaration or statement at end of input
make: *** [ov511.o] Error 1
ryan@ryan-desktop:~/ov511-1.65$ 

```

---

### Post by quelx on 2008-06-01
If you have the **kernel-headers** package installed try downloading this (since it supports the 2.6.24 kernel) and follow the instructions from the [http://alpha.dyndns.org/ov511/install.html](http://alpha.dyndns.org/ov511/install.html) page (substituting where needed)  The module you'll get when all is said and done will be called **ov51x-jpeg** instead of **ov511**

[http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.7.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.7.tar.gz)

---

### Post by ImThatNerd on 2008-06-01
> **quelx said:**
> If you have the **kernel-headers** package installed try downloading this (since it supports the 2.6.24 kernel) and follow the instructions from the [http://alpha.dyndns.org/ov511/install.html](http://alpha.dyndns.org/ov511/install.html) page (substituting where needed)  The module you'll get when all is said and done will be called **ov51x-jpeg** instead of **ov511**

[http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.7.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.7.tar.gz)

I don't believe I have kernal headers installed. So should I find that? And you suggest downloading that last link?

---

### Post by quelx on 2008-06-01
for the **linux-headers** package ```
sudo apt-get install linux-headers
```

yes use [http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.7.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.7.tar.gz)

---

### Post by ImThatNerd on 2008-06-01
> **quelx said:**
> for the **linux-headers** package ```
sudo apt-get install linux-headers
```

yes use [http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.7.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.7.tar.gz)

```
ryan@ryan-desktop:~$ sudo apt-get install linux-headers
[sudo] password for ryan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is a virtual package provided by:
  linux-headers-2.6.22-14 2.6.22-14.52
  linux-headers-2.6.22-14-generic 2.6.22-14.52
  linux-headers-2.6.24-17-xen 2.6.24-17.31
  linux-headers-2.6.24-17-virtual 2.6.24-17.31
  linux-headers-2.6.24-17-server 2.6.24-17.31
  linux-headers-2.6.24-17-rt 2.6.24-17.31
  linux-headers-2.6.24-17-openvz 2.6.24-17.31
  linux-headers-2.6.24-17-generic 2.6.24-17.31
  linux-headers-2.6.24-17-386 2.6.24-17.31
  linux-headers-2.6.24-17 2.6.24-17.31
  linux-headers-2.6.24-16-xen 2.6.24-16.30
  linux-headers-2.6.24-16-virtual 2.6.24-16.30
  linux-headers-2.6.24-16-server 2.6.24-16.30
  linux-headers-2.6.24-16-rt 2.6.24-16.30
  linux-headers-2.6.24-16-openvz 2.6.24-16.30
  linux-headers-2.6.24-16-generic 2.6.24-16.30
  linux-headers-2.6.24-16-386 2.6.24-16.30
  linux-headers-2.6.24-16 2.6.24-16.30
You should explicitly select one to install.
E: Package linux-headers has no installation candidate
ryan@ryan-desktop:~$ 

```

---

### Post by quelx on 2008-06-01
```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by ImThatNerd on 2008-06-01
> **quelx said:**
> ```
sudo apt-get install linux-headers-`uname -r`
```

```
ryan@ryan-desktop:~$ sudo apt-get install linux-headers-`uname -r`
[sudo] password for ryan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.24-17-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libmono-addins-gui0.2-cil libmono-security1.0-cil obex-data-server
  libmono-sharpzip0.84-cil sqlite libmono-system-web1.0-cil libbeagle1
  libgtkhtml3.16-cil libmono-addins0.2-cil python-pyatspi python-brlapi
  libflickrnet2.1.5-cil libzvbi-common libmono1.0-cil libmono-data-tds1.0-cil
  libmono-system-data1.0-cil sqlite3 libopenobex1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ryan@ryan-desktop:~$ 





```

Is that all fine?

---

### Post by quelx on 2008-06-01
Yes, apparently you had the headers installed all along. Go ahead with **make** using [http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.7.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.7.tar.gz)

---

### Post by ImThatNerd on 2008-06-01
> **quelx said:**
> Yes, apparently you had the headers installed all along. Go ahead with **make** using [http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.7.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.7.tar.gz)

Okay I did, I got this:

```
ryan@ryan-desktop:~$ cd /home/ryan/ov51x-jpeg-1.5.7
ryan@ryan-desktop:~/ov51x-jpeg-1.5.7$ make
make -C /lib/modules/2.6.24-17-generic/build M=/home/ryan/ov51x-jpeg-1.5.7 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'
  CC [M]  /home/ryan/ov51x-jpeg-1.5.7/ov51x-jpeg-core.o
  CC [M]  /home/ryan/ov51x-jpeg-1.5.7/ov511-decomp.o
  CC [M]  /home/ryan/ov51x-jpeg-1.5.7/ov518-decomp.o
  CC [M]  /home/ryan/ov51x-jpeg-1.5.7/ov519-decomp.o
  LD [M]  /home/ryan/ov51x-jpeg-1.5.7/ov51x-jpeg.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/ryan/ov51x-jpeg-1.5.7/ov51x-jpeg.mod.o
  LD [M]  /home/ryan/ov51x-jpeg-1.5.7/ov51x-jpeg.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'
ryan@ryan-desktop:~/ov51x-jpeg-1.5.7$ 



```

I guess I will try the other instructions now that it seems it worked.

---

### Post by ImThatNerd on 2008-06-01
Okay well I was suppose to become root it says by su - . So I did and got this, so I skipped it.

```
ryan@ryan-desktop:~$ su -
Password: 
su: Authentication failure
ryan@ryan-desktop:~$ 
ryan@ryan-desktop:~$ 

```

Then I do the first step on two and type lspci and get the list of everything. I assume it is UHCI since there was no OHCI. So I type the stuff it says and get this:

```
ryan@ryan-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:08.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
ryan@ryan-desktop:~$ modprobe usb-uhci
FATAL: Module usb_uhci not found.
ryan@ryan-desktop:~$ modprobe uhci
FATAL: Module uhci not found.
ryan@ryan-desktop:~$ 

```

Really sorry for all the problems tonight.

---

### Post by quelx on 2008-06-01
For the commands it wants you to run as root just put **sudo** in front, ignore the usb stuff, unless **lsmod|grep usb** comes up empty```
sudo make install
sudo modprobe ov51x-jpeg
```

---

### Post by ImThatNerd on 2008-06-01
> **quelx said:**
> For the commands it wants you to run as root just put **sudo** in front, ignore the usb stuff, unless **lsmod|grep usb** comes up empty```
sudo make install
sudo modprobe ov51x-jpeg
```

Alright great. It looks like it is working fine on the xawtv. I could have sworn quality was better with it on windows, but I am just happy it is working. Thank you do much. I hope I don't have any more problems.

---

### Post by ImThatNerd on 2008-06-01
Yeah it shows video on xawtv, but when I go to stickam.com the webcam site it doesn't recognize the video I guess since it is all black. Though I right clicked and checked settings and it had this webcam selected. I will try other sites then.

---

### Post by ImThatNerd on 2008-06-01
Does anyone know why it shows on xawtv and Ubuntu recognizes it, but no websites recognize I have a web cam plugged in? I know when I had windows it did...

thanks

---


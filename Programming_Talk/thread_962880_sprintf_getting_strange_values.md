---
title: "sprintf: getting strange values"
date: 2008-10-29
forum: Programming Talk
---

### Post by tom66 on 2008-10-29
```

DEBUG (2): Going to read 87944 bytes of data. 
DEBUG (3): Percent complete: 0.00% (read 4294967 bytes, mean value: 0)
DEBUG (4): Percent complete: 0.00% (read 4294839 bytes, mean value: 0)
DEBUG (5): Percent complete: 0.00% (read 4294829 bytes, mean value: 0)
DEBUG (6): Percent complete: 0.00% (read 4294827 bytes, mean value: 0)
DEBUG (7): Percent complete: 0.00% (read 4294894 bytes, mean value: 0)
DEBUG (8): Percent complete: 0.00% (read 4294843 bytes, mean value: 0)
DEBUG (9): Percent complete: 0.00% (read 4294756 bytes, mean value: 0)
DEBUG (10): Percent complete: 0.00% (read 4294837 bytes, mean value: 0)
DEBUG (11): Percent complete: 0.00% (read 4294905 bytes, mean value: 0)
DEBUG (12): Percent complete: 0.00% (read 4294782 bytes, mean value: 0)
DEBUG (13): Percent complete: 0.00% (read 4294937 bytes, mean value: 0)
DEBUG (14): Percent complete: 0.00% (read 4294736 bytes, mean value: 0)
DEBUG (15): Percent complete: 0.00% (read 4294916 bytes, mean value: 0)
DEBUG (16): Percent complete: 0.00% (read 4294743 bytes, mean value: 0)
DEBUG (17): Percent complete: 0.00% (read 4294833 bytes, mean value: 0)
DEBUG (18): Percent complete: 0.00% (read 26 bytes, mean value: 0)
DEBUG (19): Percent complete: 0.00% (read 4294843 bytes, mean value: 0)
DEBUG (20): Percent complete: 0.00% (read 4294673 bytes, mean value: 0)
DEBUG (21): Percent complete: 0.00% (read 4294859 bytes, mean value: 0)
DEBUG (22): Percent complete: 0.00% (read 4294916 bytes, mean value: 0)
DEBUG (23): Percent complete: 0.00% (read 4294746 bytes, mean value: 0)
DEBUG (24): Percent complete: 0.00% (read 2 bytes, mean value: 0)
DEBUG (25): Percent complete: 0.00% (read 4294701 bytes, mean value: 0)
DEBUG (26): Percent complete: 0.00% (read 4294893 bytes, mean value: 0)
DEBUG (27): Percent complete: 0.00% (read 4294874 bytes, mean value: 0)
DEBUG (28): Percent complete: 0.00% (read 4294796 bytes, mean value: 0)
DEBUG (29): Percent complete: 0.00% (read 0 bytes, mean value: 0)
DEBUG (30): Percent complete: 0.00% (read 4294815 bytes, mean value: 0)
DEBUG (31): Percent complete: 0.00% (read 4294792 bytes, mean value: 0)
DEBUG (32): Percent complete: 0.00% (read 4294921 bytes, mean value: 0)
DEBUG (33): Percent complete: 0.00% (read 4294634 bytes, mean value: 0)
DEBUG (34): Percent complete: 0.00% (read 4294966 bytes, mean value: 0)
DEBUG (35): Percent complete: 0.00% (read 4294701 bytes, mean value: 0)
DEBUG (36): Percent complete: 0.00% (read 68 bytes, mean value: 0)
DEBUG (37): Percent complete: 0.00% (read 4294730 bytes, mean value: 0)
DEBUG (38): Percent complete: 0.00% (read 4294938 bytes, mean value: 0)
DEBUG (39): Percent complete: 0.00% (read 4294864 bytes, mean value: 0)
DEBUG (40): Percent complete: 0.00% (read 4294634 bytes, mean value: 0)
DEBUG (41): Percent complete: 0.00% (read 4294876 bytes, mean value: 0)
DEBUG (42): Percent complete: 0.00% (read 4294894 bytes, mean value: 0)
DEBUG (43): Percent complete: 0.00% (read 4294738 bytes, mean value: 0)
DEBUG (44): Percent complete: 0.00% (read 97 bytes, mean value: 0)
DEBUG (45): Percent complete: 0.00% (read 4294647 bytes, mean value: 0)
DEBUG (46): Percent complete: 0.00% (read 40 bytes, mean value: 0)
DEBUG (47): Percent complete: 0.00% (read 4294617 bytes, mean value: 0)
DEBUG (48): Percent complete: 0.00% (read 4288861 bytes, mean value: 0)
DEBUG (49): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (50): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (51): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (52): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (53): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (54): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (55): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (56): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (57): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (58): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (59): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (60): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (61): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (62): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (63): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (64): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (65): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (66): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (67): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (68): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (69): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (70): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (71): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (72): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (73): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (74): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (75): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (76): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (77): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (78): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (79): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (80): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (81): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (82): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (83): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (84): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (85): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (86): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (87): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (88): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (89): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (90): Percent complete: 0.00% (read 4288205 bytes, mean value: 0)
DEBUG (91): Closing file handle... 
DEBUG (92): Freeing memory... 

```

The values are incorrect, but why?

Here is the code:

```

if(pos % 1000 == 0)
{
	sprintf(_debug_msg, "Percent complete: %2.2f%% (read %d bytes, mean value: %d)", 
		(pos / wd.data_length) * 100, pos, total / 1000);
	DEBUG(_debug_msg);
	total = 0;
}

```

Any help appreciated.

---

### Post by WW on 2008-10-29
You haven't shown us all the code, but I'm 99.99% sure that pos, wd.data_length and total are integers.  Integer division in C does not give you a floating point number; it gives you an integer. Think of grade school division: 11/4 = 2, with a remainder of 3.  It appears that pos is always less than wd.data_length, so pos/wd.data_length is always 0.  You can fix this by casting one of the variables to be, say, a double.  Or, in the case of total/1000, it is sufficient to change the denominator to 1000.0.

Try this instead:
```

	sprintf(_debug_msg, "Percent complete: %2.2f%% (read %d bytes, mean value: %f)", 
		((double)pos / wd.data_length) * 100, pos, total / 1000.0);

```

---


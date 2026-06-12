---
title: "File Decoding"
date: 2008-04-01
forum: Programming Talk
---

### Post by themusicwave on 2008-04-01
So I have this file that I have no idea what encoding it is using.  It may not even be using one.

It may just be a binary dump or something I will be unable to read.

However, I'd like to know if it is possible to decode it.  It's a log file taken from a PLC at work that the PLC manufacturer won't tell me how to read.  I suspect it might simply be a matter of finding the write encoding.

Here is the output python gives me for the file:
> logFile.read()
'MachineView datalogger data file.\x00\x0e\x00\xe0\x93\x04\x00\x88\x15\x03\x00\x00\x00\x00\x00\x88\x15\x03\x00h\xa0\xeaG\xbf\x02\x00\x00\x01\x00\x0b\x00\x00\x00\x00\x00h\xa0\xeaG\xbf\x02\x00\x00\x02\x00\n\x00\x00\x00\x00\x00h\xa0\xeaG\xbf\x02\x00\x00\x03\x00\n\x00\x00\x00\x00\x00h\xa0\xeaG\xbf\x02\x00\x00\x04\x00\n\x00\x00\x00\x00\x00h\xa0\xeaG\xbf\x02\x00\x00\x05\x00\n\x00\x00\x00\x00\x00h\xa0\xeaG\xbf\x02\x00\x00\x06\x00\x0b\x00\x00\x00\x00\x00h\xa0\xeaG\xbf\x02\x00\x00\x07\x00\x0b\x00\x00\x00\x00\x00h\xa0\xeaG\xbf\x02\x00\x00\x08\x00\x0b\x00\x00\x00\x00\x00h\xa0\xeaG\xbf\x02\x00\x00\t\x00\x0b\x00\x00\x00\x00\x00h\xa0\xeaG\xbf\x02\x00\x00\n\x00\x0b\x00\x00\x00\x00\x00h\xa0\xeaG\xbf\x02\x00\x00\x0b\x00\x0b\x00\x00\x00\x00\x00h\xa0\xeaG\xbf\x02\x00\x00\x0c\x00\n\x00\x01\x00\x00\x00h\xa0\xeaG\xbf\x02\x00\x00\r\x00\n\x00\xe2\x02\x00\x00h\xa0\xeaG\xbf\x02\x00\x00\x0e\x00\x0b\x00\x00\x00\x14\xc2h\xa0\xeaG\xbf\x02\x00\x00\x0f\x00\n\x00\x00\x00\x00\x00h\xa0\xeaG\xbf\x02\x00\x00\x10\x00\n\x00\x00\x00\x00\x00h\xa0\xeaG\xbf\x02\x00\x00\x11\x00\n\x00\xf8\xff\xff\xffh\xa0\xeaG\xbf\x02\x00\x00\x12\x00\n\x00^\x01\x00\x00h\xa0\xeaG\xbf\x02\x00\x00\x13\x00\n\x00^\x00\x00\x00h\xa0\xeaG\xbf\x02\x00\x00\x14\x00\n\x00\xbb\x00\x00\x00h\xa0\xeaG\xbf\x02\x00\x00\x15\x00\x0b\x00\x00\x00\x00\x00h\xa0\xeaG\xbf\x02\x00\x00\x16\x00\x0b\x00\x00\x00\x00\x00h\xa0\xeaG\xbf\x02\x00\x00\x17\x00\x0b\x00\x00\x00\x00\x00h\xa0\xeaG\xbf\x02\x00\x00\x18\x00\x0b\x00\x00\x00\x00\x00h\xa0\xeaG\xbf\x02\x00\x00\x19\x00\x0b\x00\x00\x00\x00\x00h\xa0\xeaG\xbf\x02\x00\x00'

I'll attach the file itself.  It is a Windows file so I hope that isn't an issue, I don;t see why it should be.

So can anyone decode it?  If you can how did you do it?  If I knew the encoding I could decode it myself, but nothing I tried has worked.

Should pose a fun challenge for someone.  I don't absolutely need the info in the file, but I am just plain curious.

Thanks,

Jon

---

### Post by nick_h on 2008-04-01
To decode the file you will probably have to know what data is likely to be stored.  Then you can look at it with a hex editor and see if you recognise anything.  There seems to be the character "G" repeating every 16 bytes which may give you a clue to a record size.

---

### Post by themusicwave on 2008-04-01
I know what it contains somewhat.

I have a programmer from the manufacturer to convert the file to a comma separated value file or a dbase file. 

I was just trying to skip the conversion step and read the file directly.

It should have a pattern of something like:
Date, Time, variable name, value, some junk I don't need

There should be about 300,000 of these records.  That's what the dbase file looks like anyways.  The times should also be 15 seconds apart.


Like it said it's more curiosity than anything.

---

### Post by heikaman on 2008-04-01
hi here's what i could find out after looking at the file in a hex editor:
1- the file is in big-endian format.

2- each record is 16 bytes long.

3- the MSB of the counter "which is actually the LSB because it's in big-endian" counts up to 31 "0x1f" when it reaches 31 it starts over and the seconds field is increased by 15, like this:

```

 <?>           <seconds>       <?>        <counter>
00 00 00 00  68 a0 ea 47  bf 02 00 00  1d 00 0a 00 
00 00 00 00  68 a0 ea 47  bf 02 00 00  1e 00 0a 00 
00 00 00 00  68 a0 ea 47  bf 02 00 00  1f 00 0a 00 
46 01 00 00  77 a0 ea 47  c4 02 00 00  01 00 03 00 
00 00 00 00  77 a0 ea 47  c4 02 00 00  02 00 02 00 
```

4- i think that the records is somehow divided into blocks each block is 31 records long, and maybe each block belongs to one item. Also, the first field is "almost" the same for each block of records.


and it was actually fun :mrgreen:

---

### Post by themusicwave on 2008-04-01
Thanks for the insight, I am glad you enjoyed it!

I can confirm that the CSV file had 31 tags per date and time set.

So there should be sets of 31.

The 15 increment you see is because the timer is set to log data every 15 seconds.

Still little hope of cracking it, but interesting!

Thanks for the ideas/contributions.

---

### Post by heikaman on 2008-04-02
> **themusicwave said:**
> 
Still little hope of cracking it, but interesting!

it's actually not that difficult, if u can convert the file to CSV "the same file" and post it i maybe able to help u more, maybe write a decoder for u.

---

### Post by nick_h on 2008-04-02
> **heikaman said:**
> it's actually not that difficult, if u can convert the file to CSV "the same file" and post it i maybe able to help u more, maybe write a decoder for u.

Not only is it not that difficult you almost gave all the details required in your last post.  themusicwave wanted a date, time, variable name and value.  The column that you called seconds is both the date and time in standard unix time format (number of seconds since midnight 01-JAN-1970).  The variable name is not recorded but there is a variable number (counter).  The only thing left to do is find the value column and associate the values with the variable names.  This would be easy to do with a copy of the data for a few specific times.

---


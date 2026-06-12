---
title: "some success with se, but need help finding blank line"
date: 2011-03-18
forum: Programming Talk
---

### Post by PaulHuffman on 2011-03-18
A colleague was faced with a problem of 804 ASCII files and he needed to extract the tabular data out of the first part and the last part into Excel spread sheets. He couldn't figure out a way using Windows tools to do this. I told him he needed Linux tools and sed was his answer.  Since I could see that the useful data in the first part of the file was always in lines 2-44, I was able to get the the data into new files using a shell script like:
[COLOR="RoyalBlue"][FONT="Courier New"]for file in *.lst
do 
sed '2,44!d' $file > ../Listout/$file
done[/FONT][/COLOR]

And the last part of the file by keying into the string 'Clock':
[FONT="Courier New"][COLOR="RoyalBlue"]for file in *.tab
do 
sed '/Clock/,$!d' $file > ./Tableout/$file
done[/COLOR][/FONT]

But some of these files have additional useful data in the middle of the file at the line that starts with 'blank char Record' under the line that starts with 'Supplemental'. There are a different number of lines of data that follow the header line, which makes it tricky.  I thought I could get sed to not delete the first blank line in the file, but this approach didn't work for me: 
[FONT="Courier New"][COLOR="RoyalBlue"]for file in *.tab
do 
sed '/Record/,/                    /!d' $file > ../sup/$file.sup
done[/COLOR][/FONT]

In the result, I got the lines from 'Record' to the end of file'.

It would be extra tricky to use grep first to find only the files that contained this string 'Supplemental' to pipe to sed.

Or is there even a better approach than sed in a shell script?

---

### Post by PaulHuffman on 2011-03-21
I just tried detecting the blank line with
for file in *.tab
do
sed '/Record/,/^[ ]*$/!d' $file > ../sup/$file.sup
done

but that gave me the same result, lines from Record to the end of the file. The blank line isn't exactly blank. It has a ^M only in the line. Can't clue into ^M because every line has that on the end of line.

---

### Post by gmargo on 2011-03-21
Don't try to match the ^M in the file.  It's a DOS-format file, and this will just mess up sed.

If you're looking for just the first batch of Supplemental_Data (Record up to blank line) then you can do this.  Note that I've inserted a sed command to convert the DOS-format to UNIX-format (and strip trailing space):
```

# use grep to find only the files containing "Supplemental" string
if grep -q '^Supplemental' $file ; then
        sed 's/[[:space:]]\+$//' $file | \
        sed '/^ Record/,/^$/!d' > ../sup/$file.sup
fi

```If you'd rather capture everything up to the "Clock" table, do something like this:
```

if grep -q '^Supplemental' $file ; then
        sed 's/[[:space:]]\+$//' $file | \
        sed '/^ Record/,/^St  Clock/!d' | \
        sed '/^St  Clock/d' > ../sup/$file.sup
fi

```

---

### Post by PaulHuffman on 2011-03-21
I couldn't get the first form to work. It just hung.  I thought the second form was going to work great. I put it inside my if:
```
for file in *.tab
do
if grep -q '^Supplemental' $file ; then
	sed 's/[[:space:]]\+$//' $file | \
        sed '/^ Record/,/^St  Clock/!d' | \
        sed '/^St  Clock/d' > ../sup/$file.sup
fi
done

```
Couldn't get it to run without the first sed line to convert it to unix lines, so I passed the through another loop because I'm going to give it back to DOS user:
```
for file in *.tab.sup
do 
sed 's/$/\r/' $file > $file.txt
done

```

But then I discovered there's some other lines that sometimes appear after the Supplemental data and before Clock:
```
^M
Supplemental_Data                ^M
 Record        Date     Time   Location(ft)   Gauge_Height(ft)  Rated_Flow(cfs)  Comments^M
     01  2010/04/29 09:31:10         0.000                ()           200.0117  ^M
     02  2010/04/29 09:33:33         0.000                ()           220.0128  ^M
^M
Automatic_Quality_Control_Test_(BeamCheck)^M
4/29/2010 9:31:17 AM ^M
        Noise_level_check Pass ^M
        SNR_check Pass ^M
        Peak_location_check Pass ^M
        Peak_shape_check Pass ^M
^M
St  Clock     Loc  Depth   IceD %Dep  MeasD Npts Spike     Vel   SNR Angle    Verr Bnd    Temp CorrFact MeanV   Area     Flow     %Q   ^M
()     ()    (ft)   (ft)   (ft) (*D)   (ft)   ()    ()  (ft/s)  (dB) (deg)  (ft/s)  ()  (degF)    ()  (ft/s)  (ft^2)    (cfs)     (%)   ^M
00  09:36   42.00  0.000  0.000  0.0  0.000    0     0  0.0000   0.0     0  0.0000   0    0.00  1.00  0.0000   0.000  -0.0000   -0.0^M

```

So I can't use Clock. I've got to somehow stop at that first blank line.

---

### Post by PaulHuffman on 2011-03-21
No, I was wrong. The first form worked great as long as I kept in the sed line to convert dos to unix. Stopped after the first blank line after "Record".  Then I converted them back to DOS txt files before handing them off to my DOS user.

---


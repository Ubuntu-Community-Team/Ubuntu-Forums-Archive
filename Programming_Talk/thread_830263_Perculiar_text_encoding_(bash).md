---
title: "Perculiar text encoding? (bash)"
date: 2008-06-15
forum: Programming Talk
---

### Post by aquavitae on 2008-06-15
I'm having some problem with the encoding in a file, I think...

I'm trying to compare two files, one's a pdf (created in windows) and the other is an odt. So what I did was first export the odt to pdf. Then I used the following commands on the two files to compare them
```
pdftotext -nopgbrk pdf.pdf pdf1.txt
fmt -su pdf1.txt > pdf2.txt

pdftotext -nopgbrk odt.pdf odt1.txt
fmt -su odt1.txt > odt2.txt

diff pdf2.txt odt2.txt

```
According to diff, the two resulting text files are completely different, so I looked at them in an editor and found that the the odt2.txt file contained what looked like three spaces between some words, although the fmt command should have removed them. Just in case, I also tried
```
tr -s [:blank:] ' '
```
but it made no difference. I then opened them up in a hex editor and found that the three spaces in odt2.txt corresponded to the hex [20] [c2 a0] [20] and, for comparison, the single space in pdf2.txt corresponded to just [20]. I thought this might be different encoding in the pdfs, but this shouldn't have come though pdftotext should it? Or am I misusing the commands?

Anyone have and idea what the extra space represented by 0xc2 0xa0 is and how to remove it? Otherwise, any suggestions of a better way of comparing the files?

---

### Post by odyniec on 2008-06-15
The *C2 A0* sequence is the Unicode non-breaking space character. I think all you need to do to properly compare the two files is replace all occurrences of the sequence with a plain old space, eg. using sed:
```
sed -e 's/\xc2\xa0/ /g' odt2.txt > odt3.txt
```

---

### Post by aquavitae on 2008-06-16
Thanks. That sorted it out. Unfortunately the pagenation and layout of the two docs are still too different to give a meaningful diff :(. I think I'll just go through them by hand.

---


---
title: "How can we improve on this manual PDF shrink from ~5MB to &lt;1MB in Ubuntu?"
date: 2014-02-25
forum: New to Ubuntu
---

### Post by Gustav_Toppa on 2014-02-25
I needed to upload my multi-page muilti-MB college transcripts and teste score PDFs to a job site which would not accept any files greater than 1 MB.
After a few trials and tribulations (see below), I hit upon the "pdf2djvu method of shrinking the files.

*QUESTION*:
**How can we improve upon the automation of this method to make it easier for users?**

Here's what I finally used (where I manually reduced the DPI settings, with successively smaller numbers, until the resulting file size was less than 1MB):
```

cp transcript.pdf input.pdf
pdf2djvu -d 1225 input.pdf -o temp.djvu
djvups temp.djvu temp.ps
ps2pdf temp.ps output_1225.pdf
mv output_1225.pdf transcript_1225.pdf

```

The (very manual) method I used was to arbitrarily choose a dpi (starting at 1225) and, checking if the result was less than the 1MB cutoff.
Almost always, the output PDF was much greater than 1MB (so I had to successively decrease the DPI).

Here are actual file size results, as I successively decreased the DPI in order to arrive at a final file size less than 1MB.
```

1:
total 10148
-rw-r--r-- 1 foo foo 3320249 Feb 25 16:22 input.pdf
-rw-r--r-- 1 foo foo 1764724 Feb 25 16:22 transcript_ba_1225dpi.pdf
-rw-r--r-- 1 foo foo  937441 Feb 25 16:22 transcript_ba_775dpi.pdf
-rw-r--r-- 1 foo foo 1033693 Feb 25 16:22 transcript_ba_825dpi.pdf
-rw-r--r-- 1 foo foo 1081750 Feb 25 16:22 transcript_ba_850dpi.pdf
-rw-r--r-- 1 foo foo 1129487 Feb 25 16:22 transcript_ba_875dpi.pdf
-rw-r--r-- 1 foo foo 1113623 Feb 25 16:22 transcript_ba_900dpi.pdf

2:
total 6652
-rw-r--r-- 1 foo foo 4793967 Feb 25 16:22 input.pdf
-rw-r--r-- 1 foo foo  987671 Feb 25 16:22 transcript_ms_1200dpi.pdf
-rw-r--r-- 1 foo foo 1022040 Feb 25 16:22 transcript_ms_1225dpi.pdf

3:
total 7664
-rw-r--r-- 1 foo foo 3275697 Feb 25 16:22 input.pdf
-rw-r--r-- 1 foo foo 1074322 Feb 25 16:22 lsat_1000dpi.pdf
-rw-r--r-- 1 foo foo 1460786 Feb 25 16:22 lsat_1225dpi.pdf
-rw-r--r-- 1 foo foo  993779 Feb 25 16:22 lsat_950dpi.pdf
-rw-r--r-- 1 foo foo 1034574 Feb 25 16:22 lsat_975dpi.pdf

4:
total 10540
-rw-r--r-- 1 foo foo 1262737 Feb 25 16:22 gre_1000dpi.pdf
-rw-r--r-- 1 foo foo 1726887 Feb 25 16:22 gre_1225dpi.pdf
-rw-r--r-- 1 foo foo  974821 Feb 25 16:22 gre_800dpi.pdf
-rw-r--r-- 1 foo foo 1153020 Feb 25 16:22 gre_875dpi.pdf
-rw-r--r-- 1 foo foo 1045867 Feb 25 16:22 gre_900dpi.pdf
-rw-r--r-- 1 foo foo 1157821 Feb 25 16:22 gre_950dpi.pdf
-rw-r--r-- 1 foo foo 3460385 Feb 25 16:22 input.pdf

5:
total 7856
-rw-r--r-- 1 foo foo 1157849 Feb 25 16:38 input.pdf
-rw-r--r-- 1 foo foo  720511 Feb 25 16:38 recommendation_1225.pdf
-rw-r--r-- 1 foo foo  870775 Feb 25 16:38 recommendation_1400.pdf
-rw-r--r-- 1 foo foo  964734 Feb 25 16:38 recommendation_1500.pdf
-rw-r--r-- 1 foo foo  988577 Feb 25 16:38 recommendation_1525.pdf
-rw-r--r-- 1 foo foo 1012594 Feb 25 16:38 recommendation_1550.pdf
-rw-r--r-- 1 foo foo 1058485 Feb 25 16:38 recommendation_1600.pdf
-rw-r--r-- 1 foo foo 1253935 Feb 25 16:38 recommendation_1800.pdf

```

**For the benefit of all, is there a better way that is more automated than the trial-&-error approach that I took just now?**

Note: I tried these methods also but they stunk in comparison, with respect to resulting quality for the amount of shrinkage needed.
```

$ convert input.pdf -compress Zip output.pdf
$ convert -compress JPEG -quality 100 input.pdf output.pdf
$ convert input.pdf output.jpg; convert output.jpg convert.pdf
$ gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf
$ gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/printer -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf
$ gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4  -dPDFSETTINGS=/prepress -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf  input.pdf
And, I tried to print the PDF to a PDF using the Ubuntu printer GUI.

```

---


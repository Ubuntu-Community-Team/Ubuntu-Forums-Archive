---
title: "Create A Drag And Drop Script For PDF Code"
date: 2012-05-04
forum: Programming Talk
---

### Post by AmbientOcclusion on 2012-05-04
I was trying to find a way to create some sort way to have a script run on a file if I drag the file onto it.

For example, using this pdf resize code:

```
gs -sDEVICE=pdfwrite -dPDFSETTINGS=/screen -dCompatibilityLevel=1.4 -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf
```

If I had it in some sort of script file that all I had to do was drop a pdf on it and have it be resized, that would be the solution I need.

I'm guessing that I could change
> ***input.pdf*** to ****.pdf***
Is that correct?

I remember doing this with batch files in windoze, but I am stuck in Linux.

I also don't know what type of file it would have to be.

Thanks ahead of time for any help.

---

### Post by gordintoronto on 2012-05-04
I'm not sure of the specifics, but you would need to mark the text file as executable. By convention, it would be called something.sh, but that's not mandatory.

---

### Post by AmbientOcclusion on 2012-05-05
Thanks for that.

Adding the .sh extension and making it executable definitely puts it in the right direction.

I still can't figure out a drag and drop solution.

---

### Post by AmbientOcclusion on 2012-05-05
I created a launcher, and linked it to the script. I enlarged the launcher just to make it easier to see if I was dropping it on top easier.

It appears to work, at least for drag and drop purposes.

The output is an empty pdf called output.pdf

I am wondering if it is my syntax for the input file:
```
*.pdf
```
???

Also, the weird thing is that the launcher works only once. If I try to drag and drop another pdf onto it nothing happens.

The only code in the executable script is:
```
gs -sDEVICE=pdfwrite -dPDFSETTINGS=/screen -dCompatibilityLevel=1.4 -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf *.pdf
```

Hmmm...

---


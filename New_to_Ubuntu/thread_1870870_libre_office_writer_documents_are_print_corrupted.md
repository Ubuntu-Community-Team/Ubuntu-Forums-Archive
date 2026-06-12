---
title: "libre office writer documents are print corrupted"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by carloslosgrande on 2011-10-28
Hi, I'm running 11.10 and have problems with printing a document. 
Previously I had a document printing with about 50% of the letters replaced with quotation marks [COLOR="DarkRed"]'[/COLOR]
I assumed this corruption to be limited to that document.
 other documents I tried printed ok.
 I restarted printer, restarted system, deleted document and restored from backup when document was printing no problems - none of this fixed it.

Today, I just created another, unrelated, document and this problem occurred on it too, except for any letters in bold.
previous document had no bolding.

I have no idea what this is.

Any clues?

---

### Post by fantab on 2011-10-28
> **carloslosgrande said:**
> Hi, I'm running 11.10 and have problems with printing a document. 
Previously I had a document printing with about 50% of the letters replaced with quotation marks [COLOR=DarkRed]'[/COLOR]
I assumed this corruption to be limited to that document.
 other documents I tried printed ok.
 I restarted printer, restarted system, deleted document and restored from backup when document was printing no problems - none of this fixed it.

Today, I just created another, unrelated, document and this problem occurred on it too, except for any letters in bold.
previous document had no bolding.

I have no idea what this is.

Any clues?

How do you know its not the Printer? Have you tried printing from another application, either from a webpage or gedit? What PRINTER are you using?

---

### Post by carloslosgrande on 2011-10-28
screen print from Opera works just fine.
PDF prints just fine.
printer is HP laserjet 1022

---

### Post by HermanAB on 2011-10-28
To eliminate the printer from the equation, print to a file and check it with Okular.

---

### Post by carloslosgrande on 2011-10-28
Its a libre office document - there is no option to print to file, I guess that would be the same as 'save'.
I can print it to a pdf file, which is what I just did and then it prints fine from the printer as that.

---

### Post by carloslosgrande on 2011-11-03
This problem is still occurring. It doesn't happen with every document, about one in five, and I can't see that I'm doing anything particularly different from one to another. I don't think saving as PDF and printing from that is the best solution here. 
Does anyone know what may be causing this?
Thanks,
Carl.

---

### Post by wieman01 on 2011-11-13
I have a solution for you, however, it does not stick... meaning you will have to perform these actions every time you open a new LibreOffice Writer document.

1. Open Writer document
2. Select Printer Settings -> Properties -> Device -> Printer language type
3. Set to "PostScript (Level from driver)"
4. Then print away!

The print-out should look fine now.

---

### Post by carloslosgrande on 2011-11-13
Seems to work, thanks for that Weiman!!
appreciated.
Carl.

---


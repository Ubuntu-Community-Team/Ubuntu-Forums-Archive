---
title: "Scan Textbooks with gscan2pdf"
date: 2008-07-24
forum: Outdated Tutorials &amp; Tips
---

### Post by fuhrysteve on 2008-07-24
I tried the [Quickly Scan a Textbook With a Camera]("http://www.instructables.com/id/Quickly-Scan-a-Textbook-With-a-Camera/") setup, but I just couldn't get the lighting right with my 5 megapixel camera, and everything was coming out with a glare.. besides, i wasn't particularly excited about figuring out a *good* way to crop all 600+ images and put them into a 1200+ page PDF.

So I decided just to do it the fool proof way: with a scanner.

Like most scanners, mine is capable of way higher resolution than needed for scanning books, but like all low-end flatbed scanners, it's slow.

Using gscan2pdf however, I am able to scan 5 pages per minute -- that's 4hrs for a 1200page book.

Let's do the math:
($150 textbook) + ($0 free software) / (4hrs) = ($37.50/hr) > (my $11/hr job)
BUT since I obviously own any textbook I scan, I'm not actually saving any money.

ANYHOW here's how to do the dirty deed:

Install necessary packages:
```
sudo apt-get install gscan2pdf djvulibre-bin scanadf sane libgtk2-ex-podviewer-perl unpaper
```I added a few other packages that aren't required by default, but things might be weird without them (fixes weird message @ startup, adds viewer for documentation, etc).

If you want to try the OCR (text-recognition) stuff, gscan2pdf will OCR the pdf for you:
```
sudo apt-get install tesseract-ocr tesseract-ocr-eng
```I have not had good results with any Linux OCR software though (although [some people have]("http://www.linux.com/feature/138511")). Omnipage 16 is supposedly the best OCR out there (bittorrent?), but unfortunately it's [not doing too well with WINE]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=12775") (I may have written the latest test results article). If you aren't worried about your soul after you die, i think you can run a pdf through Omnipage on somebody's M$ computer to OCR it.

You should be pretty set.. I had to mess with the settings to get it to actually scan (manually tell it "flatbed" instead of "Auto") but gscan2pdf is awesome and super simple: it numbers pages for you and everything.

Just stick the book on the scanner, click scan, then as soon as it is done press <Enter> and turn the page!



Please let me know if you've used this and have any improvements / suggestions, especially with regard to OCR stuff!

---


---
title: "CUPS PDF output file name changing"
date: 2024-05-08
forum: New to Ubuntu
---

### Post by sansal80 on 2024-05-08
[COLOR=#0C0D0E][FONT=-apple-system]Is there a way to change the CUPS PDF printer output file name? I use Ubuntu and most recent CUPS.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]I tried a script, cups-pdf.conf file, lp options but I was not able to find a way. I always get the output like this. -rw------- 1 informix informix 15532 May  8 22:31 stdin___L-job_292.pdf  but I want something like this:  stdntrns_informix_legacysparc_ %Y-%m-%d_%H-%M-%S.pdf[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]If you have a solution for this please let me know.[/FONT][/COLOR]

---

### Post by him610 on 2024-05-11
Are you attempting to print from the terminal? If so, please show us what you have tried so far between code blocks. Maybe someone can provide some direction.
 The man pages are helpful.
```
 ...lp(1)                                    OpenPrinting                                   lp(1)

NAME
       lp - print files

SYNOPSIS
       lp  [ -E ] [ -U username ] [ -c ] [ -d destination[/instance] ] [ -h hostname[:port] ]
       [ -m ] [ -n num-copies ] [ -o option[=value] ] [ -q priority ] [ -s ] [ -t title  ]  [
       -H handling ] [ -P page-list ] [ -- ] [ file(s) ]
       lp  [ -E ] [ -U username ] [ -c ] [ -h hostname[:port] ] [ -i job-id ] [ -n num-copies
       ] [ -o option[=value] ] [ -q priority ] [ **[COLOR="#FF0000"]-t title [/COLOR]**] [ -H handling ] [ -P page-list ]

```

---

### Post by sansal80 on 2024-05-17
Hello,

I get PDF output from a program. But I need to change name the PDF outputs dynamically.

I always get like this: stdin___L-job_321.pdf

**So I wrote a script: **generate_pdf_filename.sh

 #!/bin/bash
 
# PDF directory
PDF_DIR="${HOME}/PDF"
 
# Function to rename PDF files
rename_pdf_files() {
    # Get current user login
    USER=$(whoami)
    # Get hostname
    HOSTNAME=$(hostname)
    # Generate timestamp
    TIMESTAMP=$(date +'%Y-%m-%d_%H-%M-%S')
    # Construct new filename
    NEW_FILENAME="${PDF_DIR}/stdntrns_${USER}_${HOSTNAME}_${TIMESTAMP}.pdf"
    # Rename the file
    mv "$1" "$NEW_FILENAME"
}


**I updated the cups-pdf.conf file for PostProcessing**

PostProcessing /etc/cups/generate_pdf_filename.sh

**My lpoptions**

informix@legacysparc:/etc/cups$ lpoptions
copies=1 device-uri=cups-pdf:/ finishings=3 job-cancel-after=10800 job-hold-until=no-hold job-priority=50 job-sheets=none,none marker-change-time=0 name=PDF number-up=1 OutputFile=/home/informix/PDF OutputScript=/etc/cups/generate_pdf_filename.sh page-bottom=36 page-left=36 page-right=36 page-top=36 PDF=true pdftops-renderer=pdftocairo PDFVer=1.5 print-color-mode=color printer-commands=AutoConfigure,Clean,PrintSelfTestPage printer-info=PDF printer-is-accepting-jobs=true printer-is-shared=false printer-is-temporary=false printer-location printer-make-and-model='Generic CUPS-PDF Printer (w/ options)' printer-state=3 printer-state-change-time=1715973546 printer-state-reasons=none printer-type=10678348 printer-uri-supported=ipp://localhost/printers/PDF

So what is wrong? What should I do?

My PDF output file name should be like this:

stdntrns_informix_legacysparc_2024-05-16_16-33-31.pdf

---

### Post by ajgreeny on 2024-05-17
I have never had cups-pdf package installed but the print dialog that I see gives me a choice to print to my actual HP Envy printer or to "Print to file" and if I choose that it then offers pdf as the first filetype option and gives me a naming dialog.

I wonder if cups-pdf is the cause of your difficulty?

---

### Post by him610 on 2024-05-18
> I have never had cups-pdf package installed but the print dialog that I see gives me a choice to print to my actual HP Envy printer or to "Print to file" and if I choose that it then offers pdf as the first filetype option and gives me a naming dialog.
This is the way I normally print to file (PDF) also.
Just looked in Settings->Printers and discovered that I have a PDF printer listed along with my two physical printers. 
I do not know how ithe PDF printer got there. 
Did it just get auto-magically installed, or what? 
Did I miss something in the release notes?
[ATTACH=CONFIG]293787[/ATTACH][ATTACH=CONFIG]293788[/ATTACH]

---

### Post by ajgreeny on 2024-05-19
Looking at the Printer Properties for the PDF Printer it would appear that it does indeed come from your install of **cups-pdf** package.
Just as a experiment try removing the cups-pdf package, then reboot and finally try to print a document and see if the print dialog offers you the "Save to File" option.

---


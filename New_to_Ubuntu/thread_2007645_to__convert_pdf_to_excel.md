---
title: "to  convert pdf to excel"
date: 2012-06-21
forum: New to Ubuntu
---

### Post by wstay on 2012-06-21
I am using Ubuntu 10.04.
I have a pdf statement and want to convert it to an excel file format.
Is there any OCR engine/software that can accomplish this task?
Can someone please advise.

---

### Post by Zill on 2012-06-21
wstay:  One possibility is to open the pdf file with [PDFedit]("http://packages.ubuntu.com/lucid/pdfedit") then save the file as a text file.
```
sudo apt-get install pdfedit
```
You can then import the text file into OpenOffice.org (or LibreOffice) Calc etc and save the resulting spreadsheet in the desired format (eg. ods, xls etc).

To import the text file into Calc, open the Text Import dialog box via the Insert, Sheet from File menu.  Then choose either "Fixed width" or the "Separated by" options as appropriate for your data.  Note that if you use the "Fixed width" option you can set each column width via the "Fields" preview of the box.

---

### Post by Serzedo on 2012-06-21
Usually I google for online sites that do the trick. But I will try this method of PDFedit, seems good to me. :)

Thanks.

---

### Post by wstay on 2012-06-24
> **Zill said:**
> wstay: 
To import the text file into Calc, open the Text Import dialog box via the Insert, Sheet from File menu.  Then choose either "Fixed width" or the "Separated by" options as appropriate for your data.  Note that if you use the "Fixed width" option you can set each column width via the "Fields" preview of the box.

I cannot find the "Fixed width" or the "Separated by" options from the 
Insert, Sheet from File menu. Please refer to attachment.
Where can I get these options.
Please help.

---

### Post by Zill on 2012-06-24
wstay:  It looks like you chose the "Insert" menu option "Sheet", rather than "Sheet from file".  If you choose "Sheet from file" you should then get the option to select your text file and then select the delimiters as described in my earlier post.

ps.  You can still do this even by selecting the "Sheet" option.  The screen shot you posted shows the radio button "From file" and if you select this it gives the same options as I described above.

---

### Post by wstay on 2012-06-24
> **Zill said:**
> wstay:  It looks like you chose the "Insert" menu option "Sheet", rather than "Sheet from file".  If you choose "Sheet from file" you should then get the option to select your text file and then select the delimiters as described in my earlier post.

ps.  You can still do this even by selecting the "Sheet" option.  The screen shot you posted shows the radio button "From file" and if you select this it gives the same options as I described above.

Using the Insert "Sheet from file" I got screen shots: Screenshot-1 and Screenshot-2.
When I open the selected the text file ('statement' as in Screenshot-2) that I safe from a pdf file with pdfedit I got Screenshot-3.
I use the Browse button to select and open the 'statement' text file and I got back to Screenshot-3.
There are no delimiters such as "Fixed width" or the "Separated by" options as you mentioned earlier.

---

### Post by PhilGil on 2012-06-24
I believe you need to copy the text from the PDF file and paste it into a blank spreadsheet to get the column options. I'm using a newer version of Open Office/Libre Office, so YMMV.

If the statement is an image rather than embedded text, you will need OCR software.

---

### Post by Zill on 2012-06-25
wstay:  I am not quite sure which version of OOo you are using but it looks different to mine!  I use the standard Ubuntu 10.04 version so I guess you must be using a different build as the "Insert Sheet from File" appears on your "File" menu, rather than on the "Insert" menu as in my version.  However, I guess the functionality remains the same and so I have attached some screendumps to show exactly how this works on my version.

Firstly, I suggest you make *sure* you have saved your pdf file as a text file (using PDFedit).  Although this shouldn't be necessary (this is Linux after all!) you may like to save your text file with a .txt extension.  Then, using the "Nautilus" file manager, click on the text file and it *should* open in the text editor "Gedit".  If it does not then the file has not been converted properly.

Then, using the OOo "Insert Sheet from File" menu, open your text file as shown in my attachments.

This should then open the "Text Import" dialog box which will allow you to select the required delimiter.  If you choose "Fixed width" then you can drag the column markers in the data preview area at the bottom of the box.  Finally, click "OK" and your data should be on a spreadsheet, just awaiting final "tweaking" to tidy things up!

---


---
title: "Open Office spreadsheet printing issue"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by owlboxman on 2008-06-03
Hi,

I am running Gutsy (recently upgraded from Feisty) with an Epson Stylus Photo 830U (CUPS+Gutenprint v5.0.1) and have not previously had any printing problems with that combination.

I have an Open Office spreadsheet which Print Preview shows as 13 pages spread over 7 sheets. Pages 1-5 are on the first sheet and page 6 on the second. I have already printed pages 1 and 2 and am now trying to print page 6, which is of course on the second sheet, unfortunately with little success. 

I have tried a number of things;

just asking it to print page 6 results in no response from the printer (no documents queued)

asking it to print pages 5-6 (5 on the first sheet and 6 on the second) results in it printing only page 5 and not page 6

copying page 6 onto a separate part of the first sheet, and trying to print that, again results in no response

copying page 6 onto the first sheet of a completely new spreadsheet (where it is, of course, page 1) resulted in it being printed, at last!

Any help welcome (I hope I am not missing something too obvious - possibly this should be an Open Office question rather than a Ubuntu question?). I am likely to be away from my computer shortly, so may not be able to respond for a while.

---

### Post by bcom on 2008-06-03
Hello:

I don't know if this will be any help at all.  OpenOffice is, by default, configured to suppress the printing of any empty pages that have no cell contents or draw objects, cell attributes such as borders, or background colors are not considered cell contents. 

To change the default, go to Options - OpenOffice.org Calc - Print and uncheck Suppress Output of Empty Pages.

---

### Post by owlboxman on 2008-06-03
Thanks for that suggestion.

I have just tried it - unfortunately, no joy.

---

### Post by bcom on 2008-06-04
Sorry it did not work!  Have you tried either of the following:

1.  Going to File - Print and then select All Sheets as opposed to Selected sheets.
2.  Identifying which sheet page six is on, going to that sheet, finding page six and printing directly from page six in the proper sheet.

Perhaps the fact that you have 13 pages spread over different sheets is creating the problem.  If that is the case you could experiment with the different options but, maybe you have already gone this route.

You could try deleting and than adding the printer.  That might fix a problem created by the upgrade.

---


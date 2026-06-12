---
title: "mysql to csv export using php"
date: 2009-01-12
forum: Programming Talk
---

### Post by Elisei on 2009-01-12
hi everybody:

i am trying to export a table from mysql using php to have it in .csv format. The trick is that the table has text in 18 different languages (English, French, Russian, Japanese, Greek, etc). So the non-english characters are corrupt in the output file.

Is there some kind of special universal encoding that one should be using to accommodate for high language variation?

right now we have:

[PHP]
header("Content-Type: text/x-csv; chartset=utf-8");
header("Content-Disposition: attachment; filename=".$tbl.".csv");
print $csv_output;
exit;
[/PHP]

above of course works great in linux - csv file contains proper characters but the issue occurs in windows both with IE and firefox.

any suggestions are appreciated.

---

### Post by mssever on 2009-01-12
> **Elisei said:**
> Is there some kind of special universal encoding that one should be using to accommodate for high language variation?
UTF-8. Windows might want the file to begin with a byte-order mark.

---

### Post by drubin on 2009-01-12
odd I found this
header("Content-type: application/csv");
That might be required for windows. I know that windows often needs odd headers to render files correctly.

I am not on a windows PC so can't check this out. Report back and let me know?

EDIT: 
Some use header("Content-type: application/octet-stream");  but I don't like the general octet stream header..

---


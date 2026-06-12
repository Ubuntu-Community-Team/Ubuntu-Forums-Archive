---
title: "Bash Help - CSV Seperation"
date: 2009-03-04
forum: Programming Talk
---

### Post by leinad1 on 2009-03-04
Hello. I've just started a training course and the language we are learning is bash, i found this practice exercise in the online course.

I'd appreciate it lots if someone could tell me what a working model would look like. So i can look through the code and work it out.

This is the CSV file to be seperated.

ISBN,Title,Author,Category,Cost,No copies
978-0340681138,Five Get into Trouble (Famous Five),Enid Blyton,Childrens,6,3
978-1861058492,His Way: The Brian Clough Story,Patrick Murphy,Sport,6,5
978-0142301883,The Little Match Girl,Hans Christian Anderson,Childrens,3,2
978-1565924260,Learning the Vi Editor,Linda Lamb,Computing,13,1
978-0007231324,Blood Beast,Darren Shan,Horror,7,1
978-0752433660,Nottingham Forest: Champions 1977-1978,John Shipley,Sport,8,10
978-0596100292,Unix in a Nutshell,Arnold Robbins,Computing,17,2
978-0340921531,Cell,Stephen King,Horror,3,5
978-1859835135,The Legends of Nottingham Forest,Dave Bracegirdle,Sport,11,8
978-0596005955,Classic Shell Scripting,Arnold Robbins,Computing,16,4

It asks:
*create files with the names, children_books, horror_books, sports_books and computing_books. These files will have a format like...

ISBN: 978-0340681138
Author: Enid Blyton
Title: Five Get Into Trouble (Famous Five)

*Records which do not belong to any of the above categories should be printed as an error

*Summary report will be displayed on the screen and contain the following information: 
-Date
-names of files created (full path)
-total number of books processed
-total value of books

Thanks in advance to any help

---

### Post by ghostdog74 on 2009-03-04
what have you learned so far in your bash course? in pure bash, you can use while read loop to iterate your csv file, IFS (input field separator) to indicate your delimiter.eg
```

IFS=","
while read isbn title author category cost copies
do
 echo "$isbn $title $author $category $cost $copies"
done < csv_file.csv

```
pls read the bash reference guide in my sig for more on bash.

awk is another file manipulation tool you can use for such purpose.

---


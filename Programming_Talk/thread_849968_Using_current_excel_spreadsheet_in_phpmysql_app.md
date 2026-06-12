---
title: "Using current excel spreadsheet in php/mysql app"
date: 2008-07-05
forum: Programming Talk
---

### Post by pssturges on 2008-07-05
Hi,

I have an excel spreadsheet who's data I wish to use in a php/mysql site. The data is in the form of a matrix showing the distance between two locations. The first row and first column show the locations, the cells within the table show the distances between the locations. Sample attached.

The idea is that my php code will take two locations and look up the distance between them.
example: location 1 & location 5, distance = 10.

My problem is getting this data into a format that my php code can access. If it was to be in a mysql table I imagine the rows would be something like location_a, location_b, distance, but I have no idea how I would go about importing the data.

Would I be better off exporting the speadsheet to csv or a text file and accessing the data from there? The real data has aproximately 120 locations (approx 14000 entries), so manually entering the data is not an option.

Any suggestions greatly appreciated.

Phil

---

### Post by ghostdog74 on 2008-07-05
you can search google or PEAR for PHP excel classes that can allow you to read xls file direct. Another way is to use COM.

---

### Post by odyniec on 2008-07-05
Since the data is in a simple format, I'd suggest you export it to CSV. You should be able to parse it easily with explode().

---


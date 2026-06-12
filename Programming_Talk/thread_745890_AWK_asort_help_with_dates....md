---
title: "AWK asort help with dates..."
date: 2008-04-05
forum: Programming Talk
---

### Post by hopelessone on 2008-04-05
Hi all,

I'm a very limited self taught programmer and would like to sort this AWK script by date it's going through 1300 files, here's what i got:

```
awk 'BEGIN{ IGNORECASE=1; onefile="newfile.html"}
/>posted/{
  date[FILENAME]=$6
  time[FILENAME]=$7
  am[FILENAME]=$8
  store[FILENAME]+=1
  test=$6

}
/<TITLE>/{
  gsub(/<TITLE>|<\/TITLE>| - The Archives| - the BB|<META.*\"no-cache\">/,"")
  title[FILENAME]=$0
}
/<FONT SIZE="2" face="Verdana, Arial"><B>/{
  user[FILENAME]=$4
  
}

END {

[COLOR="Red"]n = asort(test)
for (a = 1; a <= n; a++) {[/COLOR]
	

	  if (i=i) {

    		
    		print "<FONT SIZE=\"2\" FACE=\"Verdana, Arial\">" date[i] " <FONT SIZE=\"2\" FACE=\"Verdana, Arial\" COLOR=\"#800080\">" time[i] " " am[i] "</FONT></FONT>" 
	  
	}

}
}' *.html
```

the dates are either 19-05-1999 or 19-05-99

I get awk: cmd. line:20: (FILENAME=003247.html FNR=87) fatal: attempt to use scalar `test' as array


n = asort(test)
for (a = 1; a <= n; a++) {

i don't understand why the error?

thanks..

---

### Post by LaRoza on 2008-04-05
Is "test" an array?

---

### Post by hopelessone on 2008-04-05
yeah it would be as the script is going through 1300 files...

---

### Post by ghostdog74 on 2008-04-05
> **hopelessone said:**
> 
n = asort(test)
for (a = 1; a <= n; a++) {

i don't understand why the error?

thanks..

i have indicated in your previous posts that asort() works on arrays. you have assigned $6 to variable "test" but not as array. You would also have read the [GNU awk manual]("http://www.gnu.org/software/gawk/manual"), have you? Look for [sorting array]("http://www.gnu.org/software/gawk/manual/gawk.html#Array-Sorting"). and what is  (i =i) ?? where did your "i" come from? it should be "a".

---

### Post by hopelessone on 2008-04-05
so...

END {
for ( a in test ) { **<< is this now assigned to an array?**

n = asort(test)
for (a = 1; a <= n; a++) {

cheers..

---

### Post by ghostdog74 on 2008-04-05
looks like you don't bother to see the link i gave you.

---

### Post by hopelessone on 2008-04-05
i did.!

must not be understanding...

it says:

The order in which an array is scanned with a `for (i in array)'  **(for ( a in test ) {)**

and 

populate the array data **(for ( a in test ) {)**
     n = asort(data)
     for (i = 1; i <= n; i++)
         do something with data[i]

well did that...

---

### Post by hopelessone on 2008-04-05
still getting errors:

/>posted/{
arr[test]=$6 **<<--Better?**

etc...

END {
for ( a in test ) {
n = asort(test)
for (a = 1; a <= n; a++) {

---

### Post by hopelessone on 2008-04-05
still says awk: cmd. line:20: (FILENAME=003247.html FNR=87) fatal: attempt to use scalar `test' as array

with this:

awk 'BEGIN{ IGNORECASE=1; onefile="newfile.html"}
/>posted/{
  date[FILENAME]=$6
  time[FILENAME]=$7
  am[FILENAME]=$8
  store[FILENAME]+=1
  arr[test]=$6

}
/<TITLE>/{
  gsub(/<TITLE>|<\/TITLE>| - The Archives| - the BB|<META.*\"no-cache\">/,"")
  title[FILENAME]=$0
}
/<FONT SIZE="2" face="Verdana, Arial"><B>/{
  user[FILENAME]=$4
  
}

END {

n = asort(test)
for (a = 1; a <= n; a++) {

  		
    		print "<FONT SIZE=\"2\" FACE=\"Verdana, Arial\">" arr[a] " <FONT SIZE=\"2\" FACE=\"Verdana, Arial\" COLOR=\"#800080\">" time[i] " " am[i] "</FONT></FONT>" 
	}  

}' *.html

why?

---

### Post by stroyan on 2008-04-05
The asort operation will sort an array by the values of the elements.
You need to create an array indexed by file name by assigning to test[FILENAME].
But asort will only sort one array and will lose the mapping between
the original order of the array and the sorted order.
What you really want is to produce an array of FILENAME values sorted by the date values.
That would give you a way to use your other arrays in data order.
To accomplish that you might create a single array of filenames indexed by date.
Since multiple html files may have the same date, you need handle collisons.
You could avoid that by making the array index be a concatanation of the date and the FILENAME.
That would still sort in date order, but have unique keys.
Then the asorti operation would be able to create a mapping array that gives the index values to the test array in date sorted order. 

Here is a version using asort that splits out a FILENAME part of a date-sorted vvalue.

```

awk 'BEGIN{ IGNORECASE=1; onefile="newfile.html"}
/>posted/{
  date[FILENAME]=$6
  time[FILENAME]=$7
  am[FILENAME]=$8
  store[FILENAME]+=1
  test[FILENAME]=$6 " " FILENAME
}
/<TITLE>/{
  gsub(/<TITLE>|<\/TITLE>| - The Archives| - the BB|<META.*\"no-cache\">/,"")
  title[FILENAME]=$0
}
/<FONT SIZE="2" face="Verdana, Arial"><B>/{
  user[FILENAME]=$4
}
END {
  n = asort(test)
  for (a = 1; a <= n; a++) {
    split(test[a],parts)
    i=parts[2]
      print "<FONT SIZE=\"2\" FACE=\"Verdana, Arial\">" date[i] " <FONT SIZE=\"2\" FACE=\"Verdana, Arial\" COLOR=\"#800080\">" time[i] " " am[i] "</FONT></FONT>" 
  }
}' *.html

```

Here is a version using asorti to map into a date-sorted index.
```

awk 'BEGIN{ IGNORECASE=1; onefile="newfile.html"}
/>posted/{
  date[FILENAME]=$6
  time[FILENAME]=$7
  am[FILENAME]=$8
  store[FILENAME]+=1
  test[$6 " " FILENAME]=FILENAME
}
/<TITLE>/{
  gsub(/<TITLE>|<\/TITLE>| - The Archives| - the BB|<META.*\"no-cache\">/,"")
  title[FILENAME]=$0
}
/<FONT SIZE="2" face="Verdana, Arial"><B>/{
  user[FILENAME]=$4
}
END {
  n = asorti(test, map)
  for (a = 1; a <= n; a++) {
    f=test[map[a]]
    print "<FONT SIZE=\"2\" FACE=\"Verdana, Arial\">" date[f] " <FONT SIZE=\"2\" FACE=\"Verdana, Arial\" COLOR=\"#800080\">" time[f] " " am[f] "</FONT></FONT>" 
  }
}' *.html

```

---

### Post by hopelessone on 2008-04-06
thanks very much for the explanation....was close but couldn't have done it without the sample code...cheers...!!

---


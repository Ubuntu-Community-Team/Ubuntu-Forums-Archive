---
title: "Update sreadsheet from command line?"
date: 2010-10-16
forum: Programming Talk
---

### Post by coolen on 2010-10-16
I'm wondering if anyone knows of a way to update a .xls spreadsheet from the command line? I simply need to insert an integer into a cell I specify at run-time.

It's not majorly important, but it would make my life just that little bit easier, and isn't that what computers are for?

Thanks in advance.

---

### Post by spjackson on 2010-10-17
> **coolen said:**
> I'm wondering if anyone knows of a way to update a .xls spreadsheet from the command line? I simply need to insert an integer into a cell I specify at run-time.

It's not majorly important, but it would make my life just that little bit easier, and isn't that what computers are for?

Thanks in advance.
I'm not aware of a direct way to do this. However, if you know perl, then CPAN has a module that can read and write .xls spreadsheets. I've only used it for write, but I believe you should be able to read, update a cell and write.

---

### Post by Xender1 on 2010-10-17
I agree with spjackson, I actually wrote some code to do just this a while ago and it is actually quite simple. In perl after ou get the CPAN module use Spreadsheet::WriteExcel; (there is also ParseExcel too).

```

#this is in my perl program so you will need the right shebang and use things 
#at the top

#creates excel object and new wksh
my $workbook = Spreadsheet::WriteExcel->new("newexcel.xls");
	my $worksheet = $workbook->add_worksheet(); #adds new worksheet

my $col = 0; my $row = 0; #you could have these passed into cmd line

$worksheet->write($row, $col, "hello!"); #write it to 0,0  on first wksh

$workbook->close(); #close excel file we just wrote

```

pretty simple that should help get you started if you want to to do it in perl

---

### Post by DaithiF on 2010-10-18
and if you prefer Python, equivalent modules for reading/writing xls files are xlrd / xlwt

---

### Post by coolen on 2010-10-19
Thanks guys. This should be enough to get me going. I don't have any aversion to Python or Perl (although I'm only familiar with the former), so I'll get going on that tonight.

Much appreciated ^_^

---

### Post by coolen on 2010-10-19
Looking into it further, it seems that neither the Perl nor Python modules are capable of writing to an existing worksheet.

There is a Ruby module that purportedly can accomplish this. I'm not familiar with it, but has anyone used this? I'm having trouble finding documentation on it.


[EDIT]

I got it. The Ruby module is the only thing I could find that allows you to both read a .xls file and make changes to it. Other modules allowed you to do both separately, but the objects for each did not seem to be compatible (the Python module could with an additional utilities package which I couldn't find in the repos).

What it doesn't do is allow you to write back to the original file. So, I had to perform a little trickery, renaming the original file then writing a new file with the original name before deleting the original.

If anyone's interested, here's what I came up with:

```
#!/usr/bin/env ruby
require 'spreadsheet'

row, col, val, file = ARGV

temp = file.split('.')
temp[temp.length-2] = temp[temp.length-2]+'_(' +(0...8).map{65.+(rand(25)).chr}.join + ')'

until !(File::exists?(temp.join('.')))
    temp[temp.length-2] = temp[temp.length-2].slice[0,temp[temp.length-2].length-10]
    temp[temp.length-2] = temp[temp.length-2]+'_(' +(0...8).map{65.+(rand(25)).chr}.join + ')'
end

File.rename(file, temp.join('.'))

book = Spreadsheet.open temp.join('.')
sheet = book.worksheet 0
sheet[Integer(row)-1,Integer(col)-1] = Integer(val)
book.write file

File.delete(temp.join('.'))
```

It requires libspreadhseet-ruby1.9.1 (there's also a 1.8 in the repos, but I didn't test it with that). It can only handle integer values at the moment (sufficient for my immediate purpose).

Also, this is only suitable for updating a single cell, or perhaps a small number. It takes a while to run due to the file I/O, and only performs one change, so trying to use this in a larger loop will take a long time.

---


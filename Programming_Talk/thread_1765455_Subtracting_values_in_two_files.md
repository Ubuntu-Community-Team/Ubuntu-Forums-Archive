---
title: "Subtracting values in two files"
date: 2011-05-23
forum: Programming Talk
---

### Post by lorenz_b on 2011-05-23
Dear community,

I have a problem here, and I want to use perl to automate this reocurring calculation:

I have files with values organized in 8 rows and 12 columns (space separated) and I want to create a new file showing the differences of the corresponding values (e.g. value row1,col1 in file1 - value row1,col1 in file2) in the same 12x8 pattern.
Could you give me ideas for tackling this problem with perl (i want to get some experience).

cheers,
Lorenz

---

### Post by r-senior on 2011-05-23
I don't know Perl, but the pseudocode would be fairly straighforward:

```

a = array_with_dimensions(8, 12)
b = array_with_dimensions(8, 12)
diff = array_with_dimensions(8, 12)

read_array_from_file(a, "filea.txt")
read_array_from_file(b, "fileb.txt")

for row = 1 to 8 do
    for column = 1 to 12 do
        diff[row][column] = a[row][column] - b[row][column]
    end
end

write_array_to_file("diff.txt", diff)

```

So all you need to figure out is

  - how to create multi-dimensional arrays
  - how to read a file
  - how to do loops
  - how to work with multi-dimensional arrays
  - how to write to a file

---

### Post by kaibob on 2011-05-24
I do not know perl and cannot fully answer your question. Perhaps with this bump, another forum member will see this thread and be of help.

For practice, I decided to write this as a bash shell script, which I have included below. It loops through each line of the two data files (data1.txt and data2.txt) and stores the individual values in array variables named data1 and data2. The actual calculations are done by the bc utility, and the results are stored in the array variable named calc and then saved in the file calc.txt. I used the bc utility because it supports floating-point calculations.

```

#!/bin/bash

while read -r -u 3 -a data1 && read -r -u 4 -a data2 ; do
  ((${#data1[*]} != ${#data2[*]})) && echo "Data mismatch" && exit 1
  for i in ${!data1[@]} ; do
    calc+=($(bc -q <<< "${data1[i]}-${data2[i]}"))
  done
  printf "%s\n" "${calc[*]}" >> calcs.txt
  unset calc i
done 3< data1.txt 4< data2.txt

```

REFERENCE POST 10
[http://ubuntuforums.org/showthread.php?t=1443689](http://ubuntuforums.org/showthread.php?t=1443689)

---

### Post by lorenz_b on 2011-05-26
Thanks a lot,

I try to get a working script from your suggestions.

L

---


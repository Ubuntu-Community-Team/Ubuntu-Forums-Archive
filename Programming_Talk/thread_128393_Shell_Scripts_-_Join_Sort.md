---
title: "Shell Scripts - Join? Sort?"
date: 2006-02-11
forum: Programming Talk
---

### Post by JustRandomName on 2006-02-11
Hi,
I am having a few problems with a shell script, maybe you guys can help me out.

I have a file called details with a list of ID and names like so:

24100321 John Smith
24100123 Jayne Doe
24100124 Dave Jones
24101124 Laura Taylor
24100111 Gary Johnson
24100222 Simon Smith
...etc...

I also have a file called results like so:
24100222
01 10
02 9
03 8
04 8
05 6
06 6
24100124
01 6
02 2
03 6
04 4
05 6
06 1
24100321
01 4
02 5
03 4
04 6
05 1
06 1
24100123
01 1
02 1
03 1
04 4
05 10
06 2

How would I match the names to the ID? I think it has something to do with join.

At the minute I am doing:

join -a1 results details > tempfile

This is matching up some id's with names (Only Jayne Doe and John Smith from the sample data), but not all of them. I suspect I have to somehow sort the data first... How can I tell sort to treat every seven lines as one record?

Also how would I get the ones that have not been matched up to be output too? something like this@

24100321 John Smith
01 4
02 5
03 4
04 6
05 1
06 1
24100123 Jayne Doe
01 1
02 1
03 1
04 4
05 10
06 2
Missing Laura Taylor


I have tried with by using the -e argument with join like so:

join -a1 -e "Missing" results details > tempfile

But it seems to get ignored.

Thanks

---

### Post by stylishpants on 2006-02-11
For each shell programmer there comes a time when you realize it is going to save you time to abandon your lovely collection of piped together commands and use a more powerful scripting language to accomplish your task.  For me at least, this problem is clearly over that line.  It's time to switch to something like Perl, Python or Ruby.

Since I'm in a Ruby kind of mood today,  here is a first shot.  It could be much shorter, but it's a good base to start from.

```

#!/usr/bin/ruby

result_file = "results.txt"
id_file = "ids.txt"
data = Hash.new {|hash,key| hash[key] = Hash.new}  # Create a new hash of hashes

# Get name, ID from file
File.open(id_file).each {|line|

	unless line.match(/^(\d+) (.*)$/)
		puts "Don't recognize this ID line: #{line}"
		next
	end
	id, name = $1, $2
	
	data[id][:name] = name
}

# Get results from file
id = 0
File.open(result_file).each {|line|

	if line.match(/^(\d+)$/)			# look for an ID string
		id = $1
		next

	elsif line.match(/(\d+) (\d+)/)	# otherwise look for a result record
		key, value = $1, $2
		data[id][key] = value

	else
		puts "Don't recognize this result line: #{line}"
	end
	
}

# Print results
incomplete = Array.new
data.keys.sort.each { |id|
	myData = data[id]
	name = myData[:name]

	# Remember the ones that are missing some data
	if 7 == myData.size 
		puts "#{id} #{name}"
		myData.keys.each { |key|
			puts "\t#{key} #{myData[key]}" unless :name == key  # (don't print the name again)
		}
	else  # this guy is missing some data - remember him for later
		incomplete << [id,name]
	end
	puts 
}

# Print names with no data
if incomplete.size > 0
	puts "These names have no data:"
end
incomplete.each { |me|
	id, name = me
	puts "#{id} #{name}"
}


```

---

### Post by jerome bettis on 2006-02-12
that time hasn't come for me yet, awk is so much fun.  there's so many ways of attacking this problem, here's my quick, dirty, and somewhat elegant solution.

this script runs on the assumption that your files have no blank lines.  if they do, it's easy to filter them out beforehand with one line of awk.  it also assumes the files are well formed and each result will have someone listed in the details file. you can have an arbitrary set of numbers instead of 7 inbetween.

```
#!/bin/bash

(cat details && echo && cat results) | awk '        # pipe the 2 files to awk,
BEGIN  {                                            # with a blank line inbetween
    i = 0;
    phase_one = 1;
}
{
    if (length($0) == 0)  {                         # total hack but it works
        phase_one = 0;
        getline;                                    # skip the blank line and start phase 2
    }
    if (phase_one)  {                               # working with the details file
        people[++i] = sprintf("%s %s", $2, $3);     # store their name into an array

        t[$1] = i;                                  # put the index for person i into
                                                    # another array indexed by their ID

    } else  {                                       # finished that, onto results file
        if (NF == 1)  {                             # assuming one field here is an ID #
            printf("%s %s\n", $1, people[t[$1]]);
            people[t[$1]] = "";                     # clear them from the list
        } else  {                                   # assuming it is a result pair
            printf("%s %s\n", $1, $2);
        }
    }
}

END  {
    for (j = 1; j <= i; ++j)  {                     # print out anybody that did not have
        if (length(people[j]) > 0)  {               # their ID in the result file
            printf("Missing %s\n", people[j]);
        }
    }
} '
```

---


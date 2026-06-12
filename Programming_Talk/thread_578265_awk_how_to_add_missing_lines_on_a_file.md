---
title: "awk: how to add missing lines on a file?"
date: 2007-10-17
forum: Programming Talk
---

### Post by CyberAngel on 2007-10-17
Hello,

I have a file like the following:

```

100    0   some-data
100    1   some-data
100    2   some-data
100    3   some-data
100    4   some-data
100    5   some-data
100    6   some-data
100    7   some-data
...
...
100    59   some-data
101    0   some-data
...
...
1304  0   some-data
1304  1   some-data
....

```

Those data are retrieved from a data logger.
In the first column it is the hour and minutes (GMT time).
In the second column these are the seconds and in the last one the date retrieved.
I want an awk script (or something else anyway but in bash scripting language) to parse the hole file for misconceptions, because it might be a single second that the data logger will not retrieve data so I want to fix the output file as follows.

What do I need the script to do:
It will be checking the first and the second columns to see if any seconds are missing and it will fill with zero data lines:
Take a look at the following example:

```

...
...
1303  58   some-data
1304  0   some-data
1304  1   some-data
1304  2   some-data
1304  3   some-data
1304  5   some-data
1304  6   some-data
...
...

```

In the above example as you can see is missing the data line for 13:03:59 and 13:04:04

So if the above is the input file I want an output file as following:

```

...
...
1303  58   some-data
1303  59   zero-data
1304  0   some-data
1304  1   some-data
1304  2   some-data
1304  3   some-data
1304  4   zero-data
1304  5   some-data
1304  6   some-data
...
...

```

Thanks!

---

### Post by CyberAngel on 2007-10-24
Anyone for this one?
I Still need it and I have not found a solution.

---

### Post by stylishpants on 2007-10-24
OK, how about this:

```

#!/usr/bin/ruby -w

require 'time'
require 'pp'

# Get a string describing the time in the logfile's format 
# Don't zero-pad the seconds field!
def time_string(time)
	time.strftime("%H%M  %S").sub(/\b0(\d)\b/, '\1 ')
end


##########################

# Get input file name from cmd line args
infile = ARGV.shift
if infile.nil?
	puts "Please supply the name of a logfile.\n"
end
unless File.exist? infile
	puts "File does not exist: #{infile}"
end
lines = IO::readlines(infile)		# Read the input file

# Parse the time on the first line in the input file
raise "Could not parse first line: #{lines.first}" unless lines.first =~ /^(\d\d)(\d\d)  (\d\d)/
hrs, min, sec = $1, $2, $3
time = Time::parse(hrs + ":" + min + ":" + sec)

# Read each input line
output_lines = Array.new
lines.each do |line|
	time_str = time_string(time)

	# Add zero-data lines for each second 
	# until the time catches up with the next line of the input file
	until line =~ /^#{time_str} /
		zero_line = time_str + "  zero-data\n"
		output_lines << zero_line

		time += 1
		time_str = time_string(time)
	end

	output_lines << line
	time += 1
end

# Write results to output file
outfile = infile + ".out"
File::open(outfile,"w") {|io| io << output_lines }
puts "Wrote '#{outfile}'"



```

---

### Post by CyberAngel on 2007-10-24
I will check this out and let you know :)
Thank you very much!

---


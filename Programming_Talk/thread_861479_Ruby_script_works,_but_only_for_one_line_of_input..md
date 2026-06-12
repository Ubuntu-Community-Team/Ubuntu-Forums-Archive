---
title: "Ruby script works, but only for one line of input.. please help"
date: 2008-07-16
forum: Programming Talk
---

### Post by jessebean on 2008-07-16
Hi, I've written the following script, which works fine for the single line provided /@line = " ... "/, but when I enter the whole csv file in place of the single line, if fails.  It doesn't seem to like my usage of /if ...split(//).length == 4/, as the error I get, trying various ways of inputting the line, is "undefined method `split' for nil::NilClass"

It even fails for entering the same two lines, but calling `split(/\n/)' seems to foul up the latter calls to `split'.

Please bear in mind that I'm at the public library, and it will help the most for a solution, rather than a hint.  I can only come here once a day, and I've already had to "work around" some security features just to paste the code from usb stick, not to mention that ubuntuforums.org seems to be the only forum I can access from the library.

```
@line = "
00001740, 29, v, 04, breathe, 0, take_a_breath, 0, respire, 0, suspire, 3, 021, *, 00005041, v, 0000, *, 00004227, v, 0000, +, 03110322, a, 0301, +, 00831191, n, 0303, +, 04080833, n, 0301, +, 04250850, n, 0105, +, 00831191, n, 0101, ^, 00004227, v, 0103, ^, 00005041, v, 0103, $, 00002325, v, 0000, $, 00002573, v, 0000, ~, 00002573, v, 0000, ~, 00002724, v, 0000, ~, 00002942, v, 0000, ~, 00003826, v, 0000, ~, 00004032, v, 0000, ~, 00004227, v, 0000, ~, 00005041, v, 0000, ~, 00006697, v, 0000, ~, 00007328, v, 0000, ~, 00017031, v, 0000, 02, +, 02, 00, +, 08, 00
"

#
# after replacing the above line with all 1xx,xxx lines,
# stating @var = @line.split(/\n/); @i = 0
# while @i < @var.length
# the script chokes.  I'm new to scripting ruby.
# Please help me solve this.
#
# Basically, it removes the appended data following /0000/
# and omits all references to parts of speech other than verb

@line_array = @line.split(", ")
@line_tokens = @line_array.length
@n = 1
@m = 0


while @m == 0
  @last_token = @line_array[@line_tokens - @n]
  if @last_token.split(//).length == 4
    @m = @line_tokens - @n
  else
    @n += 1
  end
end


@selected = String.new
@omitted = 0
@n = 4
while @n <= @m

  if @line_array[@n + 2] == 'n' or @line_array[@n + 2] == 'a' or @line_array[@n + 2] == 's' or @line_array[@n + 2] == 'r'
    @omitted += 1
    @n += 4
  elsif @line_array[@n + 2] == 'v'  
    @selected << @line_array[@n] << ", " << @line_array[@n + 1] << ", " << @line_array[@n + 3] << ", " 
    # printf "%s, %s, %s, %s, ", @line_array[@n - 2], @line_array[@n - 1], @line_array[@n], @line_array[@n + 1]
    # printf "%s, ", @line_array[@n]
    @n += 4
  else
    @selected << @line_array[@n] << ", "
    @n += 1
  end
end


@new_count = @line_array[@line_array[3].to_s.hex.to_i * 2 + 4].to_i - @omitted


printf "%s, %s, %s, %s, %s\n", @line_array[0], @line_array[1], @line_array[3], @new_count.to_s, @selected.split(", ").join(", ")

```

---

### Post by stevescripts on 2008-07-17
hmm ....

I preface by noting that I am *NOT* an accomplished ruby hacker.

I spend some of my (not so...) copious spare time these days trying
to achieve a certain level of comfort with things like, Python,
Perl (re-visited), Ruby, Lisp, et al.

Hopefully a reply might catch the eyes of someone who does real work with
Ruby.

If your purpose is to learn ruby by writing a script to parse a csv file,
keep after it, that said, there is a library (package/module, whatever the
ruby folks call it) for handling csv.  (No need to re-invent the wheel, unless you enjoy doing so...) A simple example follows:
```


#!/usr/local/bin/ruby

require 'csv'

CSV.open('test2.csv', 'r') do |row|
    p row
end


```

Of course, replace "test2.csv" with whatever file you are working with.

This just *might* give you a better place to start.

Hope this helps.

Steve

---

### Post by stylishpants on 2008-07-17
> **jessebean said:**
> Hi, I've written the following script, which works fine for the single line provided /@line = " ... "/, but when I enter the whole csv file in place of the single line, if fails.  It doesn't seem to like my usage of /if ...split(//).length == 4/, as the error I get, trying various ways of inputting the line, is "undefined method `split' for nil::NilClass"




It's difficult to help you based on the available information.  Please say what the actual intent of your code is, with small examples of the expected input and the desired output for that input.

I realize that you're at a library terminal and probably can't include an entire CSV file of input.  That's OK.  Just include a few typical lines.  Explain the breakdown of a single line, at least the parts of the line you care about.

Your current input line is gibberish to me, I can't tell where a record starts or ends.  It would be much clearer if you had a single record (ie. a collection of related data) per line.   Maybe you already do.  It's hard to tell.

BTW I did read your description:

# Basically, it removes the appended data following /0000/
# and omits all references to parts of speech other than verb

but it is ambiguous and doesn't describe the ultimate goal of the program.

Since your entire input is a single line that starts with 0000, does that mean that everything after the first 4 chars should get removed?

---

### Post by mssever on 2008-07-17
Several suggestions, in no particular order:

[LIST]
[*]Get and use ruby-debug. It's incredibly useful for tracking down these linds of problems, because you can watch the program run and see where it goes wrong. ```
sudo aptitude install rubygems ruby1.8-dev
sudo gem install ruby-debug
```Then, use it like this: ```
require 'rubygems'
require 'ruby-debug'
debugger
``` Of course, you can use it as a command-line switch. Type help for a list of commands.
[*]When you report errors, it's helpful if you include the backtrace. Since there was no line number, I can only guess where the error occurred.
[*]It looks like you're referencing a non-existent array index. When you access such an index, Array#[] returns nil, and nil doesn't respond to :length. I believe that this is a design flaw in Ruby (Python always raises an exception in such a situation); use Array#fetch instead (this also applies to Hash#[] vs. Hash#fetch). That method will raise an exception on an invalid index--which is almost always the proper behavior. Switching to Array#fetch won't solve your problem. It'll only make it easier to spot.
[*]Your code is a mess. You should only use instance variables for data that needs to be accessible from outside the method in which you're defining it. Also, I can't tell at a glance what @m and @m mean. Try a descriptive name, though I suspect that if you examine the various methods provided by Array and Enumerable, you likely won't even need them. And, I see no reason to make them instance variables, as their function appears to be purely local. Because your code is a mess, I haven't carefully parsed it; that would take too much time.
[/LIST]

---


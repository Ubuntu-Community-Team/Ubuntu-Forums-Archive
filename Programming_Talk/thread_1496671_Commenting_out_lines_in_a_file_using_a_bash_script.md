---
title: "Commenting out lines in a file using a bash script."
date: 2010-05-29
forum: Programming Talk
---

### Post by vamega on 2010-05-29
Hi.

I was wondering if anyone could help me figure out how I could comment out certain lines in a file using a bash script.

The lines I'm looking for are
```

    <IfModule mod_userdir.c>
        <Directory /home/*/public_html>
            php_admin_value engine Off
        </Directory>
    </IfModule>

```

I want to prefix every one of the above lines with a # so that the lines look like this.
```
#    <IfModule mod_userdir.c>
#        <Directory /home/*/public_html>
#            php_admin_value engine Off
#        </Directory>
#    </IfModule>

```

Does anyone know how I could do this?

---

### Post by Andrew_Grant on 2010-05-29
Any plain text editor, vi, emacs for command line or gedit or kate for gnome or KDE, will do the job.  Just remember to make sure you have permission.  For example, sudo vi <path/file> or sudo gedit <path/file>.  It is a good idea to save a copy of the file: cp <file> <file.copy> before attempting any editing.
Andrew

---

### Post by vamega on 2010-05-29
I know I could do this using any text editor.
But I was looking for a scripted way to do this.
What I need to do is identify the lines in the file, and then comment them out.

I originally thought of using sed, but I couldn't figure out how to get sed to do this.

---

### Post by AdotB on 2010-05-29
a simple way of using sed would be
```
sed "s/pattern/#pattern/" < $infile
```

heres a simple script using sed. the first argument is the input file name, all others are patterns to be commented.
```
#!/bin/bash
infile=$1
shift
while [ $# -gt 0 ]; do
    pattern=$1
    shift
    sed "s/$pattern/#$pattern/" < $infile
done

```

Unfortunately, it doesn't place the # at the beginning of the line, but right before the pattern. But maybe its a start.

Awk might work better, but i've never used it.

---

### Post by AdotB on 2010-05-29
Heres a ruby script that comments lines by regular expression or line numbers.
```
#!/usr/bin/env ruby

def usage
    puts <<EOS
Usage: #{__FILE__} [options] infile pattern1 [pattern2 ...]

  -r  --regexp                comment all lines matchinp patterns (default)
  -n  --numbers               comment by line numbers instead of patterns
  -c  --comment-mark <MARK>   use <MARK> to comment (default=`#')
  -f  --file                  input file (default is first arg)
  -h  --help                  this help
EOS
end


$comment_mark = "#"
$by_number = false
$by_regexp = true
$input_file = nil

while ARGV.any?
    case arg = ARGV.shift
    when "-r", "--regexp"
        $by_number = false
        $by_regexp = true
    when "-n", "--numbers"
        $by_number = true
        $by_regexp = false
    when "-c", "--comment-mark", "--mark"
        $comment_mark = ARGV.shift
    when "-f", "--file"
        $input_file = ARGV.shift
    when "-h", "--help"
        usage
        exit 0
    else
        if $input_file
            ARGV.unshift arg
        else
            $input_file = arg
        end
        break
    end
end

unless $input_file
    STDERR.write "no input file given\n"
    exit 1
end

line_num = 0
File.open($input_file, 'r').each_line do |line|
    line_num += 1
    ARGV.each do |pattern|
        if $by_number
            number = pattern.to_i
            if number == 0
                STDERR.write "invalid line number: `#{pattern}'\n"
                exit 1
            end
            if line_num == number
                line = $comment_mark + line
            end
        elsif $by_regexp
            if Regexp.new(pattern) =~ line
                line = $comment_mark + line
            end
        end
    end
    puts line
end

```

---

### Post by DaithiF on 2010-05-29
using sed:
```
sed '/<IfModule mod_userdir.c>/,/<\/IfModule>/s/^/#/'  somefile

```
add the -i flag to make the changes in-place to the file when you've confirmed the results are as you expected.

---

### Post by vamega on 2010-05-29
Thanks DaithiF.
That works beautifully.

---

### Post by somekool on 2012-09-25
great script, only missing an in-place option ... 


> **AdotB said:**
> Heres a ruby script that comments lines by regular expression or line numbers.
```
#!/usr/bin/env ruby

def usage
    puts <<EOS
Usage: #{__FILE__} [options] infile pattern1 [pattern2 ...]

  -r  --regexp                comment all lines matchinp patterns (default)
  -n  --numbers               comment by line numbers instead of patterns
  -c  --comment-mark <MARK>   use <MARK> to comment (default=`#')
  -f  --file                  input file (default is first arg)
  -h  --help                  this help
EOS
end


$comment_mark = "#"
$by_number = false
$by_regexp = true
$input_file = nil

while ARGV.any?
    case arg = ARGV.shift
    when "-r", "--regexp"
        $by_number = false
        $by_regexp = true
    when "-n", "--numbers"
        $by_number = true
        $by_regexp = false
    when "-c", "--comment-mark", "--mark"
        $comment_mark = ARGV.shift
    when "-f", "--file"
        $input_file = ARGV.shift
    when "-h", "--help"
        usage
        exit 0
    else
        if $input_file
            ARGV.unshift arg
        else
            $input_file = arg
        end
        break
    end
end

unless $input_file
    STDERR.write "no input file given\n"
    exit 1
end

line_num = 0
File.open($input_file, 'r').each_line do |line|
    line_num += 1
    ARGV.each do |pattern|
        if $by_number
            number = pattern.to_i
            if number == 0
                STDERR.write "invalid line number: `#{pattern}'\n"
                exit 1
            end
            if line_num == number
                line = $comment_mark + line
            end
        elsif $by_regexp
            if Regexp.new(pattern) =~ line
                line = $comment_mark + line
            end
        end
    end
    puts line
end

```

---

### Post by sisco311 on 2012-09-25
RIP, old thread.

[[img]http://ompldr.org/tYnpyNw[/img]](http://ompldr.org/vYnpyNw)

---


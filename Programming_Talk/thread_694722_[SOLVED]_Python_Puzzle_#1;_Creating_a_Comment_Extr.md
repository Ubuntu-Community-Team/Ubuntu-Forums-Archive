---
title: "[SOLVED] Python Puzzle #1; Creating a Comment Extractor"
date: 2008-02-12
forum: Programming Talk
---

### Post by 1337455 10534 on 2008-02-12
Not strictly a puzzle, but I'm so used to using Python for different purposes this was a great break! For example; I have never used len() in my code up until this point XD.
**SO here is the challenge:**
Create a script that will take a (source) document and remove all comments from it.
I admit it was trickier than I thought;
```

from easygui import *
cc = ccbox("Welcome to rm# (GUI Version).\nThis program will remove all of the comments from a file.\nWhich file would you like to un-comment?")
if cc == 0:
	exit(0)
readFile = fileopenbox()
commentChar = enterbox("What comment type would you like to remove from your file?\nFor example, if it is in Python, you would enter '#', or in C++, you would enter '/'")
origFile = open("%s" % readFile,"r")
lines = origFile.readlines(); origFile.close();
finalFile = open("%s_rm#" % readFile,"w")
finalFile.write(''); finalFile.close();
finalFile = open("%s_rm#" % readFile,"a")
totalLines = len(lines); currentLine = 0
while currentLine != totalLines:
	str(lines[currentLine])
	hasComment = lines[currentLine].find('%s' % commentChar)
	if hasComment >= 0:
		currentLine = (currentLine+1)
	elif hasComment < 0:
		hasEmpty = lines[currentLine].find('\n')
		if hasEmpty == 0:
			currentLine = (currentLine+1)
		elif hasEmpty != 0:
			finalFile.write("%s" % lines[currentLine])
			currentLine = (currentLine+1)
finalFile.close()
msgbox("Finished. The file without comments is %s_rm#.\nThe original file is unmodified." % readFile)

```

Edit; I guess you could use EasyGUI well in this case

---

### Post by Caduceus on 2008-02-12
I'm not clued up on Python, but that's supposed to be easy? [The language] looks really hard to understand to me :S This coming from a C++ user.

Sorry to go off topic, though.

---

### Post by pmasiar on 2008-02-12
It is not easy to read because it is not Python :-) It is closer to Perl, IMHO.

As they say, Real Programmer (tm) can write FORTRAN code in any language. :-)

ie canonical reading and processing of all lines of a file in Python is:

[php]
for line in file('filename'):
    # process line
[/php]

---

### Post by 1337455 10534 on 2008-02-12
> 
for line in file('filename'):
    # process line 

Dam*! I had to resort to a crude hack by storing all of the lines into a list and the calling them..
Very sorry about the readability issues with my code, an utter beginner would run away (though I would still describe myself as one).

Caduceus; I tried writing a bit of C++ once, and it did its job very well. However, the program I wrote was a clone of a program I wrote in Python, and the Python version was a third of the size! My point is that Python takes a more simplistic approach to everything, whereas C++ appears more systematic. Case in point;
```

print """
blah blach
blach
"""

```
Puts
> 
blah blach
blach
, wheras you'd need
```

#include <iostream>
using std::cout;
int main (void) {
... cout << "\nblah blach\n";
... cout << "blach\n";
... return(0);
}

```

Speaking of which, it would be awesome if someone could clone this script in a language they prefer (perhaps, C, C++, Perl, Ruby, i dunno). I would love to learn from something practical like that!

---

### Post by Quikee on 2008-02-12
This should do something very similar if I am not mistaken:

[PHP]
commentString = "#"

inputFile = open("test.txt", "r")
lines = inputFile.readlines()
inputFile.close()

outputFile = open("test.txt", "w")
for line in lines:
    strippedLine = line.strip()
    if not strippedLine.startswith(commentString):
        outputFile.write(line)
[/PHP]

---

### Post by 1337455 10534 on 2008-02-12
Could you explain 
> 
for line in lines:
    strippedLine = line.strip()
    if not strippedLine.startswith(commentString):
        outputFile.write(line) 

In particular, the 'for' method. And doesn't strip() require a 'chars' arguement?
I interpret the last 2 lines as; if the line doesn't start with a comment, write it to the file..
Is 'not' even a Python keyword?
Boy, I'm clueless.

---

### Post by pmasiar on 2008-02-12
strip() with no arguments strips whitespace chars: space, \n, \t etc. Many functions have default arguments, you can do it too, it is simple.

To get better clue you may want to read docs, or some book. They show many common idioms.

In your shell, type 'import this', and meditate on the zen wisdom.
Relevant to your case is: "There is one obvious way to do it right".
So if it is not obvious, it is not right :-)

---

### Post by Caduceus on 2008-02-12
> **1337455 10534 said:**
> Caduceus; I tried writing a bit of C++ once, and it did its job very well. However, the program I wrote was a clone of a program I wrote in Python, and the Python version was a third of the size! My point is that Python takes a more simplistic approach to everything, whereas C++ appears more systematic. 

I don't disagree, oftentimes I'd like to simplify my programs by not having all that "include" and "using" lark, but I won't complain because I just love the language. I've tried Python, VB, Ruby and Java (doing VB at college, I didn't choose it ;) ) and it was the only thing I truly liked. I would learn Ruby, but it's OO and learning two paradigm-identical languages is discouraged?

---

### Post by 1337455 10534 on 2008-02-12
@Caduceus; All languages serve their purpose. Even VB ;), and they are just an end to a means :). At least in my opinion. 
The new version I posted is more readable too!

@pmasair; If I used strip then, all of the indentation would go away, which is not desirable. Granted, a string the program that contains "#" or "/" is in danger, but even that can be changed to where hasComment >= 0: is hasComment == 0:.

---

### Post by pmasiar on 2008-02-12
> **1337455 10534 said:**
> the Python version was a third of the size! My point is that Python takes a more simplistic approach to everything, whereas C++ appears more systematic. 

Python is not less systematic. It just handles for you many details which C++ forces programmer to juggle.

---

### Post by 1337455 10534 on 2008-02-12
I was comparing simple and systematic, like apples and oranges. I wasn't trying to make a broad statement about either language, or to reach a real conclusion, just stating how it seemed to me.
Python often flows more easily than C(++), but a language can be simple and systematic at the same time :).

---

### Post by Jimmy_r on 2008-02-12
> Speaking of which, it would be awesome if someone could clone this script in a language they prefer (perhaps, C, C++, Perl, Ruby, i dunno). I would love to learn from something practical like that!

These should remove the most obvious comments such as
```

a = "a" # a comment
# another comment

```

In python
```
comment_string = '#'
input_file = "test.txt"
output_file = "changed.txt"
output_lines = []

for line in file(input_file).readlines():
    if comment_string in line:
        new_line = line.split(comment_string)[0]
        if new_line.strip() != "":
            output_lines.append(new_line)
    else: output_lines.append(line)

file(output_file, 'w').writelines(output_lines)
```

In ruby
```
comment_string = '#'
input_file = "test.txt"
output_file = "changed.txt"
output_lines = []

File.open(input_file).each do |line|
    if line[comment_string]
        new_line = line.split(comment_string)[0]
        if new_line.strip() != ""
            output_lines.push(new_line)
        end
    else output_lines.push(line)
    end
end

fout = File.open(output_file, 'w')
fout.puts output_lines
fout.close
```
In java
```

import java.io.*;

class CommentRemover {
    public static void main(String[] args) {
        String commentString = "#";
        String inputFile = "test.txt";
        String outputFile = "changed.txt";
        String line;

        try{
            FileInputStream fstream = new FileInputStream(inputFile);
            DataInputStream in = new DataInputStream(fstream);
            BufferedReader br = new BufferedReader(new InputStreamReader(in));
            FileWriter fw = new FileWriter(outputFile);
            BufferedWriter out = new BufferedWriter(fw);
            while ((line = br.readLine()) != null){
                if (line.indexOf(commentString) != -1){
                    String newLine = line.split(commentString)[0];
                    if (newLine.trim() != ""){
                        out.write(newLine);
                        out.newLine();
                    }
                }
                else{
                    out.write(line);
                    out.newLine();
                }
            }
            in.close();
            out.close();
        }
        catch (Exception e){
            System.err.println("Error: " + e.getMessage());
        }
    }
}
```

However, to strip all possible comments out while respecting strings would be a bit trickier. Consider the following:
```
#!/usr/bin/env python
# This is a comment, but the above line is not

def test():
    """This is a 
    comment
    for the function test()
    ''' " " "
    """
    print "This is a string with a # character in it"
    print "This too: \
# This continues the string on previous line"

    print ("This is " # This is a comment
           "a string")

    print """
          This is a string, 
          #not a comment.
          """
test()
```

---

### Post by slavik on 2008-02-12
the following should work  for any scripting language where comments start with # :)

```

#!/usr/bin/perl

open $in, "code.sh" or die $!;
open $out, ">code.sh.out" or die$!;

while (<$in>) {
  s/#[^!].*$//;
  print $out $_;
}

```

---

### Post by ghostdog74 on 2008-02-12
basic model.
```

awk -F"#" '/#!/{print}/^ *#/{next}{print $1}' file

```

---

### Post by Wybiral on 2008-02-13
Extra credit to anyone who can make it more with normal comments AND docstring-style triple-quote comments. Jimmy_r also brings up a good point (you can't just ignore the rest of the line, there are exceptions such as being in a quote).

---

### Post by Jimmy_r on 2008-02-13
This should respect strings and preserve the 
"#!/usr/bin/env python".

```
input_file = "test.txt"
output_file = "changed.txt"

def remove_comments(text):
    new_text = ""
    comment_char = "#"
    single_quote = "'"
    quote = '"'
    searching = False
    inside_comment = False
    searching_match = ""
    
    for i, char in enumerate(text):
        if searching:
            if text[i:i+len(searching_match)] == searching_match:
                searching = False
                inside_comment = False
            if not inside_comment:
                new_text += char
        else:
            if char == comment_char:
                if i <= 10 and text[i:i+2] == "#!":
                    new_text += char
                else:
                    searching = True
                    inside_comment = True
                    searching_match = "\n"
            elif char == quote or char == single_quote:
                searching = True
                new_text += char
                if text[i:i+3] == (single_quote*3 or quote*3):
                    searching_match = text[i:i+3]
                else:
                    searching_match = text[i]
            else:
                new_text += char
    return new_text


text = file(input_file).read()
text = remove_comments(text)
file(output_file, 'w').write(text)
```

---

### Post by ruy_lopez on 2008-02-13
Ugly C version, respects quotes and shebangs.
```

#define _GNU_SOURCE
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

FILE *open_fp(char *);
int uncomment_lines(FILE *);
int has_comment(char *);
void process_chunks(char *, size_t);
int shebangs(char *);
int isquoted(char *);
void print_upto(char *, char *);
void handle_shebangs(char *);

int main(int argc, char *argv[]) 
{
	FILE	*fp;

	if (argc == 1) {
		fp = open_fp(NULL);
		uncomment_lines(fp);
		return 1;
	}
		
	fp = open_fp(argv[1]);
	uncomment_lines(fp);
	fclose(fp);

	if (ferror(stdout)) {
		fprintf(stderr, "%s: error writing stdout\n", argv[0]);
		return (2);
	}
	return (0);
}

FILE *open_fp(char *path) 
{
	FILE *fp;

	if (path == NULL)
		return (stdin);

	if ((fp = fopen(path, "r")) == NULL) {
		fprintf(stderr, "can't open file '%s'\n", path);
		exit (1);
	} else {
		return (fp);
	}
}

int uncomment_lines(FILE *fp)
{
	char	*line = NULL;
	size_t	len = 0;
	ssize_t read;

	while ((read = getline(&line, &len, fp)) != -1) {
		if (has_comment(line)) {
			process_chunks(line, len);
		} else {
			printf("%s", line);
		}
	}
	return 0;
}

int has_comment(char *line)
{
	char *str;

	if ((str = strchr(line, '#')) == NULL) 
		return 0;
	return 1;

}

void process_chunks(char *line, size_t len)
{
	char c = '#', *cp, *cpr;

	cp = strchr(line, c); 			/* first instance of # */
	cpr = strrchr(line, c); 		/* last instance */
	if (cp == cpr && cp == line) { 		/* single # at start of line */
		if (shebangs(line))  
			printf("%s", line);
		else 
			return;
	}
       	if (cp == cpr && cp != line) {		/* single # somewhere else */
		if (isquoted(cp - 1)) 
			printf("%s", line);
		else
			print_upto(cp, line); 	/* its a comment */
	}
	if (cp != cpr) { 			/* more than one # */
		if (isquoted(cpr - 1)) {  
			printf("%s", line);
			return;
		}
	
		if (cp == line && shebangs(cp)) /* comment after shebang */
			handle_shebangs(line);
		if (cp == line)			/* multiple ### on one line */
			return;
	
		else				
			print_upto(cpr, line);	/* default prints upto last # */
	}
}

void handle_shebangs(char *line) 
{
	char chunk[strlen(line) + 1], *cps, *cpn;
	size_t n;
	int i = 0;
	
	if (strstr(line, "#!/") != line)
		return;

	cps = strchr(line, '/');
	cpn = strchr(cps, '#');
	n = strlen(line) - strlen(cpn);

	strncpy(chunk, line, strlen(line) + 1);
	for (i = 0; i < n; i++) {
		printf("%c", chunk[i]);
	}
	printf("\n");
}


void print_upto(char *p, char *line)
{
	size_t n;
	char chunk[strlen(line) + 1];
	int i = 0;
	
	n = strlen(line) - strlen(p);
	strncpy(chunk, line, strlen(line) + 1);
	for (i = 0; i < n; i++) {
		printf("%c", chunk[i]);
	}
	printf("\n");
}

int isquoted(char *chunk)
{
	char *str;

	if ((str = strstr(chunk, "'#'")) != NULL)
		return 1;
	else if ((str = strstr(chunk, "\"#\"")) != NULL)
		return 1;
	else
		return 0;
}

int shebangs(char *chunk)
{
	char *str;
	if ((str = strstr(chunk, "#!/")) != NULL) 
		return 1;
	return 0;
}

```

EDIT: Ghostdog74 looks like the winner.

---

### Post by Jimmy_r on 2008-02-13
Here we go, safe comment and docstring removal.
It also properly handles strings like this one:
```
print "This is a string \
# that continues on the next line"
```
So, what do I win? :p

```
input_file = "comments.py"
output_file = "changed.py"

def is_docstring(text, last_linebreak, location):
    if text[last_linebreak+1:location-1].strip() == "":
        return True
    return False

def is_shebang(text, location):
    return location <= 10 and text[location:location+2] == "#!"

def remove_comments(text):
    new_text = ""
    character_to_match = ""
    skip_quotes = 0
    inside_comment = False
    inside_quote = False
    inside_triple_quote = False
    inside_docstring = False
    for i, char in enumerate(text):
        if char == "\n":
            last_linebreak = i
        if inside_docstring:
            if skip_quotes:
                skip_quotes -= 1
            elif text[i-3:i] == character_to_match:
                inside_docstring = False
                new_text += "\n"
        elif inside_comment:
            if char == "\n":
                inside_comment = False
                new_text += "\n"
        elif inside_quote:
            new_text += char
            if char == character_to_match:
                inside_quote = False
        elif inside_triple_quote:
            new_text += char
            if skip_quotes:
                skip_quotes -= 1
            else:
                if text[i-3:i] == character_to_match:
                    inside_triple_quote = False
        else:
            if char == "#":
                if is_shebang(text, i):
                    new_text += char
                else:
                    inside_comment = True
            elif char == '"' or char == "'":
                if text[i:i+3] == "'''" or text[i:i+3] == '"""':
                    character_to_match = text[i:i+3]
                    skip_quotes = 3
                    if is_docstring(text, last_linebreak, i):
                        inside_docstring = True
                    else:
                        inside_triple_quote = True
                else:
                    inside_quote = True
                    character_to_match = text[i]
                if not inside_docstring:
                    new_text += char
            else:
                new_text += char
    return new_text

text = file(input_file).read()
text = remove_comments(text)
file(output_file, 'w').write(text)
```

---

### Post by ruy_lopez on 2008-02-13
> **Jimmy_r said:**
> 
It also properly handles strings
So, what do I win? :p

What do you win? From me you win a confession, that mine doesn't handle strings properly.

And a lifetime's supply of these ###

---

### Post by Jimmy_r on 2008-02-13
> **ruy_lopez said:**
> What do you win? From me you win a confession, that mine doesn't handle strings properly.

And a lifetime's supply of these ###

Heh, sounds fine. My code could use a few extra #'s at places :)

---

### Post by dwblas on 2008-02-13
> @pmasair; If I used strip then, all of the indentation would go away,
Just to clean up loose ends, note that pmasair uses a different string for the stripped line, and then writes the original, indented line.```
for line in lines:
    strippedLine = line.strip()
    if not strippedLine.startswith(commentString):
        outputFile.write(line)
```

---


---
title: "How do I..."
date: 2008-01-25
forum: Programming Talk
---

### Post by shifty2 on 2008-01-25
I'm learning python slowly and have been making a basic GUI word-count type thing for the last day or so, using pyGTK. 

I am at the point where I want to publish the results of the word count on the screen. I thought it would be just be a case of using:
[PHP]        self.textbuffer.set_text(my function)[/PHP]
However, my function is of the form
[PHP]"%s, %d" % example, number[/PHP]
which is not a string, so I'm not able to do that. Is there a simple way of converting that into a string or should I try going about it a totally different way?

Cheers for any help,
Adam

---

### Post by LaRoza on 2008-01-25
To convert to a string, use the str() method. It returns the string.

---

### Post by Wybiral on 2008-01-25
The modulus operator on a string returns a string. Try this:

```

"%s, %d" % (example, number)

```

The right-hand side needs to be a tuple for multiple arguments.

---

### Post by shifty2 on 2008-01-26
Oops, that was my bad in copying the code, I did have the brackets there my actual code. I had tried using "str" before, but my data type is "none" so it just returns "none". The few lines of offending code are below:
[PHP]    def printReport(self):
        print "In %s, there were %d words, %d paragraphs and %d lines"% \
            (self.filename, self.word_count,  self.paragraph_count, self.line_count)


    def AnalyzeEvent(self, widget):   

        D = Document(raw_input("Please enter the location of the file that you would like to analyse: \n"))
        D.generateStatistics()
        D.printReport()
        self.textbuffer.set_text(??)[/PHP]

---

### Post by Quikee on 2008-01-26
Method printReport just prints the report in the console, you have to return the text (now the function name is wrong).

[PHP]    def printReport(self):
        report = "In %s, there were %d words, %d paragraphs and %d lines"% 
            (self.filename, self.word_count,  self.paragraph_count, self.line_count)
        print report
        return report


    def AnalyzeEvent(self, widget):   
        D = Document(raw_input("Please enter the location of the file that you would like to analyse: \n"))
        D.generateStatistics()
        self.textbuffer.set_text(D.printReport())  [/PHP]

---

### Post by shifty2 on 2008-01-26
That worked perfectly, thank you. Though it would have been something obvious like that...

---


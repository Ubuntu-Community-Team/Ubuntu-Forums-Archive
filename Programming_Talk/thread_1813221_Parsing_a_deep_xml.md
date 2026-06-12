---
title: "Parsing a deep xml"
date: 2011-07-27
forum: Programming Talk
---

### Post by RobikShrestha on 2011-07-27
I have an xml file as given below. This xml file has got words. I need to search articles for these words and then, mark the word according to its <weight> and <subcategory>.
I have to use java. What would be the best way to parse the xml. Please give me some idea.

<?xml version="1.0" encoding="UTF-8"?>

<root>
    <category name="National">
        
        <subCategory name="Accident">
            <term weight="3">
                <word>accident</word>
                <word>accidents</word>
               
            </term>
            
            <term weight="2">
                <word>died</word>
                <word>dead</word>
            </term>
        </subCategory>
        
        <subCategory name="Crime">
            <term weight="3">
                
                <word>armed outfit</word>
                <word>firing</word>
               
            </term>
                
            <term weight="2">
                
                <word>intimidation</word>
                <word>security agencies</word>
                <word>law and order</word>
            </term>
        </subCategory>
   
        <subCategory name="Education">
            <term weight="3">
                <word>education</word>
                <word>school</word>
                <word>books</word>
                <word>education fair</word>
            </term>
          
            <organization weight="4">
                <word>PABSON</word>
            </organization>
        </subCategory>
   
        <subCategory name="Health">
       
            <term weight="3">
                <word>health</word>
                <word>medical</word>
                <word>patients</word>
            </term>
        </subCategory>
    </category>
    
    <category name="Sports">
        <subCategory name="Badminton">
            <term weight="3">
                <word>badminton</word>
                <word>shuttler</word>
                <word>shuttlers</word>
            </term>
        </subCategory>
        
        <subCategory name="Basketball">
            <term weight="4">
                <word>basketball</word>
            </term>
            
            <person>
                <word>Bipendra Maharjan</word>
            </person>
        </subCategory>
    
        <subCategory name="Golf">
            <person weight="4">
                <word>Deepak Thapa Magar</word>
                <word>Deepak Acharya</word>
               </person>
                
            <term weight="4">
                <word>golf</word>
            </term>
                
            <organization weight="4">
                <word>Gokarna Golf Club</word>
                <word>Nepal Professional Golf Association</word>
                <word>Surya Nepal Masters</word>
            </organization>
        </subCategory>
        
        <subCategory name="Swimming">
            <person weight="5">
                <word>Shreya Dhital</word>
                <word>Karishma Karki</word>
               </person>
            
            <term weight="3">
                <word>swimming</word>
                <word>breaststroke</word>
                <word>backstroke</word>
            </term>
            
            <term weight="2">
                <word>freestyle</word>
                <word>butterfly</word>
           
            </term>
        </subCategory>
        
        <subCategory>
            <person weight="5">
                <word>Kumar Adhikari</word>
                <word>Jitendra Pariyar</word>
                <word>Ivanho Lissanevitch</word>
            </person>
        </subCategory>
        
        <subCategory name="Volleyball">
            <person weight="5">
                <word>Sipora Gurung</word>
                <word>Manju Gurung</word>
                <word>Pratichhya Gurung</word>
            </person>
        </subCategory>
    </category>
    
    <category name="Business">
        <organization weight="4">
            <word>Khetan Group</word>
            <word>Vaidya's Group</word>
           
        </organization>
        
        <term weight="3">
            <word>budget</word>
            <word>finance minister</word>
           
            <word>grant</word>
        </term>
    </category>

</root>

---

### Post by cgroza on 2011-07-27
I am sure there are plenty of XML parsers for Java. You don't have to navigate the tree yourself, if that was the thing you were trying to do.

---

### Post by era86 on 2011-07-27
You could look into some Java libraries for parsing XML, there are many.  Start here:

[http://www.ibiblio.org/xml/books/xmljava/chapters/ch05s02.html#d0e7095](http://www.ibiblio.org/xml/books/xmljava/chapters/ch05s02.html#d0e7095)

From there, I would look at the API documentation for one of them and maybe Google some quick examples.  This is a common Java problem, so the solution can't be that hard to find.

Goodluck!

---

### Post by myrtle1908 on 2011-07-28
I've parsed alot of XML in my time and I've used many many different Java parsers.  I like dom4j the best ...

[http://dom4j.sourceforge.net/](http://dom4j.sourceforge.net/) (current version)
[http://dom4j.sourceforge.net/dom4j-1.6.1/](http://dom4j.sourceforge.net/dom4j-1.6.1/) (old website)
[http://dom4j.sourceforge.net/dom4j-1.6.1/guide.html](http://dom4j.sourceforge.net/dom4j-1.6.1/guide.html)

---

### Post by Arndt on 2011-07-28
> **RobikShrestha said:**
> I have an xml file as given below. This xml file has got words. I need to search articles for these words and then, mark the word according to its <weight> and <subcategory>.
I have to use java. What would be the best way to parse the xml. Please give me some idea.

<?xml version="1.0" encoding="UTF-8"?>

<root>
    <category name="National">
        
        <subCategory name="Accident">
            <term weight="3">
                <word>accident</word>
                <word>accidents</word>
               
            </term>
            
            <term weight="2">
                <word>died</word>
                <word>dead</word>
            </term>
        </subCategory>
        
        <subCategory name="Crime">
            <term weight="3">
                
                <word>armed outfit</word>
                <word>firing</word>
               
            </term>
                
            <term weight="2">
                
                <word>intimidation</word>
                <word>security agencies</word>
                <word>law and order</word>
            </term>
        </subCategory>
   
        <subCategory name="Education">
            <term weight="3">
                <word>education</word>
                <word>school</word>
                <word>books</word>
                <word>education fair</word>
            </term>
          
            <organization weight="4">
                <word>PABSON</word>
            </organization>
        </subCategory>
   
        <subCategory name="Health">
       
            <term weight="3">
                <word>health</word>
                <word>medical</word>
                <word>patients</word>
            </term>
        </subCategory>
    </category>
    
    <category name="Sports">
        <subCategory name="Badminton">
            <term weight="3">
                <word>badminton</word>
                <word>shuttler</word>
                <word>shuttlers</word>
            </term>
        </subCategory>
        
        <subCategory name="Basketball">
            <term weight="4">
                <word>basketball</word>
            </term>
            
            <person>
                <word>Bipendra Maharjan</word>
            </person>
        </subCategory>
    
        <subCategory name="Golf">
            <person weight="4">
                <word>Deepak Thapa Magar</word>
                <word>Deepak Acharya</word>
               </person>
                
            <term weight="4">
                <word>golf</word>
            </term>
                
            <organization weight="4">
                <word>Gokarna Golf Club</word>
                <word>Nepal Professional Golf Association</word>
                <word>Surya Nepal Masters</word>
            </organization>
        </subCategory>
        
        <subCategory name="Swimming">
            <person weight="5">
                <word>Shreya Dhital</word>
                <word>Karishma Karki</word>
               </person>
            
            <term weight="3">
                <word>swimming</word>
                <word>breaststroke</word>
                <word>backstroke</word>
            </term>
            
            <term weight="2">
                <word>freestyle</word>
                <word>butterfly</word>
           
            </term>
        </subCategory>
        
        <subCategory>
            <person weight="5">
                <word>Kumar Adhikari</word>
                <word>Jitendra Pariyar</word>
                <word>Ivanho Lissanevitch</word>
            </person>
        </subCategory>
        
        <subCategory name="Volleyball">
            <person weight="5">
                <word>Sipora Gurung</word>
                <word>Manju Gurung</word>
                <word>Pratichhya Gurung</word>
            </person>
        </subCategory>
    </category>
    
    <category name="Business">
        <organization weight="4">
            <word>Khetan Group</word>
            <word>Vaidya's Group</word>
           
        </organization>
        
        <term weight="3">
            <word>budget</word>
            <word>finance minister</word>
           
            <word>grant</word>
        </term>
    </category>

</root>

I've been only a fairly casual user of XML, so this answer may not be complete, but you have in principle two approaches: use routines to read the whole XML document into a tree structure; or write code which will handle individual constructs in the tree (elements, comments, etc.) and call a parser routine which in turn will call your code, which lets you build the tree yourself, handle specific elements, or do something entirely different.

In the first approach, you can traverse the tree yourself, but you can also use XPath expressions to simply collect the information you want. XPath is worth knowing.

---

### Post by RobikShrestha on 2011-07-28
Thanks for the replies:
For now I parsed the tree using w3c.org.dom.
i.e. went through each node and collected the keywords.
For each collection of keywords I assigned a "category", "subcategory" and "weight".

---


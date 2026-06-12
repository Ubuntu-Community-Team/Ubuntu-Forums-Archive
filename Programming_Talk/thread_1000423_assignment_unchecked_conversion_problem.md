---
title: "assignment unchecked conversion problem"
date: 2008-12-02
forum: Programming Talk
---

### Post by james_anderson on 2008-12-02
hi guys, i'm new here and I was hoping someone could help me, I' doing an assignment in java when I ran upon these warnings

Warning: C:\Users\Soud\Desktop\JAVA\New Folder\HistoryManager.java:58: warning: [unchecked] unchecked conversion
found   : java.util.ArrayList
required: java.util.ArrayList<java.lang.String>
File: C:\Users\Soud\Desktop\JAVA\New Folder\HistoryManager.java  [line: 73]
Warning: C:\Users\Soud\Desktop\JAVA\New Folder\HistoryManager.java:73: warning: [unchecked] unchecked call to add(int,E) as a member of the raw type java.util.ArrayList
File: C:\Users\Soud\Desktop\JAVA\New Folder\HistoryManager.java  [line: 77]
Warning: C:\Users\Soud\Desktop\JAVA\New Folder\HistoryManager.java:77: warning: [unchecked] unchecked conversion
found   : java.util.ArrayList
required: java.util.ArrayList<comp202.fall2008.a5.util.Document>
File: C:\Users\Soud\Desktop\JAVA\New Folder\HistoryManager.java  [line: 82]
Warning: C:\Users\Soud\Desktop\JAVA\New Folder\HistoryManager.java:82: warning: [unchecked] unchecked conversion
found   : java.util.ArrayList
required: java.util.ArrayList<comp202.fall2008.a5.util.Document>

I am not really sure what they mean or what exactly I'm doing wrong, the files i imported should work but I don't know what I'm doing wrong? can anyone help me
__________________________________________________________________

import java.util.ArrayList;
import comp202.fall2008.a5.util.Document;
import comp202.fall2008.a5.filter.DocumentFilter;

public class HistoryManager{
   
    ArrayList <Document> browser_history;
    
    public HistoryManager(){
    browser_history = new ArrayList();}
            
    public boolean add(Document toAdd){
    if(toAdd==null)
      {System.out.println("The element cannot be NULL.");
       return false;}
        
    int index = ListUtilities.indexOf(browser_history, toAdd); 
    
    if(index>=0){
       Document found = browser_history.get(index);
       if(found.getLastAccess().compareTo(toAdd.getLastAccess())<0)
         {browser_history.remove(index);
          browser_history.add(toAdd);
          return true;}}
    else
      {browser_history.add(toAdd);
       return true;}
   
    return false;}
    
    public boolean remove(Document toRemove){
    if(toRemove==null)
      {System.out.println("The element cannot be NULL.");
       return false;}
     
    int index = ListUtilities.indexOf(browser_history, toRemove);
    
    if(index==-1){
       System.out.println("The document is not present in the History List");
       return false;}
    else
      {browser_history.remove(index); 
       return true;}}
    
    public ArrayList <String> getAllHosts(){
    
    int browser_size = browser_history.size();
    ArrayList array = new ArrayList(browser_size);
    
    int i=0;
    while (i<browser_size){
    Document newdoc = browser_history.get(i);
    
    array.add(i, newdoc.getHost());  
    i++;}
    
    return array;}
               
    public ArrayList <Document> getAllDocuments(DocumentFilter doc_filter){
    
    int size = browser_history.size();
    ArrayList array = new ArrayList(size);
    
    int added =0;
    int i=0;
    
    while (i<size){
    
    Document newdoc = browser_history.get(i);
    
    if(doc_filter.accept(newdoc)); 
      {array.add(added, newdoc);  
       added++;}
    i++;}
    
    return array;}
    
    public ArrayList <Document>  getAllDocuments(){
    
    int history_size = browser_history.size();
    ArrayList <Document> new_array = new ArrayList(history_size);
    
    int added =0;
    int i=0;
    
    while (i<history_size){
    
    Document doc = browser_history.get(i);
    new_array.add(added, doc);  
    added++;
   
    i++;}
    
    return new_array;}
    
    public int getNumberDocuments(){
    return browser_history.size();}
}
_______________________________________________________________

---

### Post by dwhitney67 on 2008-12-02
What's with the semi-colon at the end of this line??
```

if(doc_filter.accept(newdoc)); 

```

Also, why are you slapping the closing curly-bracket '}' at the end of statements?  Don't you realize that it makes your code hard to read?  Flex your muscles and press that 'enter' key on your keyboard before typing the closing bracket.

---

### Post by Tony Flury on 2008-12-03
Also, for future reference, inbed your code in CODE tags (click the # or <> buttons above) when you post code next, that way the formatting is preserved.

---


---
title: "Problem running script within an app"
date: 2011-05-03
forum: Programming Talk
---

### Post by nakul777 on 2011-05-03
Hi All,


I need to run an executable  which i got from University of Edinburgh. I have to pass various  parameters to it as follows:-

File to run (Executable)  :/home/nakul/moses/mosesdecoder/trunk/moses-cmd/src/moses 

The parameters:"-f  /home/nakul/moses/mosesdecoder/trunk/scripts/training/moses-scripts/scripts-20110405-1055/training/corpus/tuning/mert/moses.ini","-v","2".

The output and the intermediate steps(like loading of other files etc.)  of this executable (moses), i want them in a textfield/TextArea.  

When i run this executable from outside the application, i get following  results and intermediate calls. 

Command:-echo  " what is the main obstacle in your work ?"| TMP=/tmp  /home/nakul/moses/mosesdecoder/trunk/moses-cmd/src/moses -f  /home/nakul/moses/mosesdecoder/trunk/scripts/training/moses-scripts/scripts-20110405-1055/training/mert/moses.ini  

the intermediate and final results after executing this command are as  follows:-

filePath:  /home/nakul/moses/mosesdecoder/trunk/scripts/training/moses-scripts/scripts-20110405-1055/training/model/phrase-table.gz  
Finished loading phrase tables : [13.000] seconds 
IO from STDOUT/STDIN 
Created input-output object : [13.000] seconds 
Translating: what is the main obstacle in your work ? 
 
Collecting options took 0.000 seconds 
Search took 0.200 seconds 
BEST TRANSLATION: &#2325;&#2381;&#2351;&#2366; &#2340;&#2369;&#2350;&#2381;&#2361;&#2366;&#2352;&#2375; obstacle|UNK|UNK|UNK &#2325;&#2366;&#2350; &#2350;&#2369;&#2326;&#2381;&#2351; ?  [111111111]  [total=-104.119] <<-16.000, -6.000, -100.000, -1.609,  0.000, -3.530, 0.000, -1.946, -5.590, -43.510, -10.792, -14.615,  -0.992, -5.737, 4.999>> 
&#2325;&#2381;&#2351;&#2366; &#2340;&#2369;&#2350;&#2381;&#2361;&#2366;&#2352;&#2375; obstacle &#2325;&#2366;&#2350; &#2350;&#2369;&#2326;&#2381;&#2351; ? 
Translation took 0.200 seconds 
Finished translating 
End. : [13.000] seconds 

**So i want all the result mentioned above to be placed within a  TextArea **
for this i have following java code :-
```

Process p1,p2,p3; 
        String s=null,s2=null,kk=null,s1[]; 
        s=jTextField1.getText(); 
        System.out.println(s); 
        jTextArea1.append("Input String is::"); 
        //jTextArea1.append(s); 
 
 
        try 
        { 
 
        jTextArea1.append("Source Sentences are :"); 
        jTextArea1.append(null); 
 
 
        jTextArea1.append(jTextField1.getText()); 
        jTextArea1.append(null); 
 
        jTextArea1.append("Calling Moses Decoder...\n\n"); 
 
        String [] arg1={"echo","$s", "|TMP=/tmp","/home/nakul/moses/mosesdecoder/trunk/moses-cmd/src/moses","-f /home/nakul/moses/mosesdecoder/trunk/scripts/training/moses-scripts/scripts-20110405-1055/training/corpus/tuning/mert/moses.ini","-v","2"}; 
 
        System.out.println(s); 
        Process pro2=Runtime.getRuntime().exec(arg1); 
        InputStream o1=pro2.getInputStream(); 
        byte[] bytes1 = new byte[4096]; 
        for (;;) 
        { 
            int nread = o.read(bytes1); 
            if (nread == -1) break; 
 
            jTextArea1.append(new String(bytes1, 0, nread)); 
        } 
 
        }catch(Exception e){ 
 
            System.out.println(e); 
        } 
 
    }


```The above code does not run to give the desires output....

Please tell how to solve this problem...

---


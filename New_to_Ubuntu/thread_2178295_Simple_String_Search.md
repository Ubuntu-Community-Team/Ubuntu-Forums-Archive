---
title: "Simple String Search"
date: 2013-10-02
forum: New to Ubuntu
---

### Post by Coffeetree on 2013-10-02
I've been looking for a simple way to look up a String in a file that  has a lot of words or Strings. There is a lot of examples out there, but  wanted one without a lot of concatenation. I was just going to use a  Scanner Object to open and then read the file using a while loop. Sorry  if there is already one of these questions out there.

---

### Post by Vaphell on 2013-10-02
what about the grep command in terminal? grep pattern file

---

### Post by Coffeetree on 2013-10-10
Sorry for the delaid response, i was going to respond but never did. Nevertheless, that is a good command and i wrote it down thinking it will be useful later when i'm looking for a file that installed and could not find. I should have let you all know that I was working in NetBeans and needed that JAVA code to write the while loop. When looking around on the net i found lots but was not what i needed. Again sy for the delay and this is what I found that worked well for what i was doing. 

                double totalmpg = 0;
                double totalgas = 0; //setting values to 0
                double totalMisc = 0;
                while (salesLogSC.hasNext()) {  // there is a Scanner here

                    salesmanDate = salesLogSC.nextLine();
                    name = salesLogSC.nextLine();
                    salesmanMiles = salesLogSC.nextDouble();
                    salesmanGas = salesLogSC.nextDouble();
                    salesmanMisc = salesLogSC.nextDouble();
                    endofInfo = salesLogSC.nextLine();
                    salesLogSC.nextLine();
    /*Then i closed the file and worked with the data from the file*/

---


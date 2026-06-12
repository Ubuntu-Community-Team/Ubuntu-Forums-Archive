---
title: "Java: Assigning each line from a text file to a variable"
date: 2008-12-03
forum: Programming Talk
---

### Post by Igniteflow on 2008-12-03
I'm able to print the content of the file which contains one integer or char per line, but I'd like to store each line as a variable to use in an algorithm.  Can anyone point me in the right direction?  Adding the values to a char[] array would work, otherwise manually assigning each line as an individual char or string would be fine too as they could be easily converted as needed.  Here is what I have right now:

[php]
      try{
        FileInputStream fstream = new FileInputStream("data.txt");
        DataInputStream in = new DataInputStream(fstream);
        BufferedReader br = new BufferedReader(new InputStreamReader(in));
        String strLine;
    
    //Read File Line By Line
    while ((strLine = br.readLine()) != null)   
    {
      System.out.println (strLine);
    }
    in.close();
    } catch (Exception e) {      
    System.err.println("Error: " + e.getMessage());
    }
  }
[/php]

I'm thinking the println statement in the while loop need replacing, but I can't get it to work.

---

### Post by cl333r on 2008-12-03
```

try {
	FileInputStream fstream = new FileInputStream("data.txt");
	DataInputStream in = new DataInputStream(fstream);
	BufferedReader br = new BufferedReader(new InputStreamReader(in));
	String strLine;
	java.util.ArrayList<String> list = new java.util.ArrayList<String>();

	while ((strLine = br.readLine()) != null) {
		list.add(strLine);
	}

	//examples
	System.out.println( "the first line is: " + list.get( 0 ) );
	System.out.println( "the third line is: " + list.get( 2 ) );


	in.close();
}
catch(Exception e) {      
	System.err.println("Error: " + e.getMessage());
}

```

---


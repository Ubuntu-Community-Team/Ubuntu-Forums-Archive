---
title: "Help!  java.util.NoSuchElementException: No line found"
date: 2017-06-07
forum: Programming Talk
---

### Post by esahhana on 2017-06-07
Sorry to ask again. I know this has been answered before but i tried what was suggested and i cant seem to sort the error.

Exception in thread "main" java.util.NoSuchElementException: No line found
	at java.util.Scanner.nextLine(Unknown Source)
	at TestsManager.getTestsList(TestsManager.java:33)
	at MultistartIG.main(MultistartIG.java:40)


this is what the TestManager class looks like


 public static ArrayList<Test> getTestsList(String testsFilePath)
    {   
    	ArrayList<Test> list = new ArrayList<Test>();


        try
        {  
        	FileReader reader = new FileReader(testsFilePath);
            Scanner in = new Scanner(reader);
            // The two first lines (lines 0 and 1) of this file are like this:
            //# instance | maxRouteCosts | serviceCosts | maxTime(sec) | ...
            // A-n32-k5       10000000          0              120       ...
            while( in.hasNextLine() )
            {   
            	String s = in.next();
                if (s.charAt(0) == '#') // this is a comment line
                    in.nextLine(); // skip comment lines
                else
                {   
                	String instanceName = s; // e.g.: A-n32-k5
                    int maxRouteCosts = in.nextInt(); // maxCosts in any route
                    int serviceCosts = in.nextInt(); // marginal costs per service
                    int maxTime = in.nextInt(); // max computational time (in sec)
                    int nIter = in.nextInt(); // # of iterations (internal loop)
                    String distrib = in.next(); // statistical distribution
                    float firstParam = Float.parseFloat( in.next() );//in.nextFloat(); // distribution parameter
                    float secondParam = Float.parseFloat( in.next() );//in.nextFloat(); // distribution parameter
                    int seed = in.nextInt(); // seed for the RNG
                    //If seed is 0 , get seed value of MAC address
                    if( seed == 0 )
                    {   MACSeed rand = new MACSeed();
                        seed = rand.getSeedOfMAC();
                    }
                    
                  //------- BEGIN: Stochastic Demands
                    String sDistrib = in.next(); // vehicle capacity
                    float k = in.nextFloat(); // vehicle capacity
                    float variance = in.nextFloat(); // variance for the lognormal distribution
                    int firstIter = in.nextInt(); // Iters for the short average
                    int secondIter = in.nextInt(); // Iters for the final average
                    //------- END: Stochastic Demands
                    //int nVehicles = in.nextInt();
                    Test aTest = new Test(instanceName, maxRouteCosts, serviceCosts,
                            maxTime, nIter, distrib, firstParam, secondParam, seed, 0,
                            sDistrib, k,  variance, firstIter, secondIter ); //, nVehicles);
                    list.add(aTest);
                }
            }
          //  in.close();
       
            reader.close();
            
        }
        catch (IOException exception)
        {   
        	System.out.println("Error processing tests file: " + exception);
        }
        return list;
    }
  
}

---

### Post by Rocket2DMn on 2017-06-13
I'll give this a shot since nobody else has replied.  First, please wrap code segments in [noparse]```
 
```[/noparse] tags - it makes it way easier to read.

I suspect that your first call to next() actually gets text from the first line, which hasNextLine() returned true for because nothing had been processed yet.  So when you try to call nextLine() a couple of lines later, there aren't any more lines to read after starting to process the single line.  In short, don't do any next()-like calls after checking hasNextLine() except calling nextLine().  It may be easier to just load each line into a string by calling nextLine(), then parse that string yourself by splitting on whitespace.

---

### Post by esahhana on 2017-06-15
Thank you for taking out time to reply. I found the problem was with the test text file where the some data was missing. I have now corrected that is it is working as expected.

---


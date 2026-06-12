---
title: "java program with oop design"
date: 2009-11-05
forum: Programming Talk
---

### Post by nathang1392 on 2009-11-05
im trying to work the kinks out and get some advice on how to do some things. there are clearly errors in this code, but im trying to work them out. my program is supposed take some information and use it to calculate someone's carbon footprint. here are some of the instructions:> 5.  The program should be written in OOP 
      format using a tester class. 
  6.  For the data structure, use either an array of 
      objects or an ArrayList. 
  7.  Create a minimum of five different objects. 
  8.  Your CO2 footprint should account for the 
      following: 
       • annual estimate of gasoline used 
       • annual estimate of electricity used 
       • annual household waste produced 
       • annual household waste recycled 
       • replacement of incandescent bulbs 
  9.  The constructor should include the following parameters: 

       • annual gasoline used 
       • average electricity bill and average electricity price 
       • number of people in home 
       • recycle paper, plastic, glass, or cans (Booleans) 
       • number of light bulbs replaced 


alright i have gotten far, i haven't yet implemented oop design because honestly i don't know how. here is how far i am with my code. i have most of the methods for the calculations worked out.
```
public class CO2Footprint
{
public double[] calculateGasEmissions(int [] gas){
        double[] gasFootprint = new double[5];
        for(int counter = 0; counter <= 5; counter++){
           gasFootprint[counter] = 19.3565 * gas[counter];

                }
                      return gasFootprint;
        }
            
      public double[] calculateElectricityEmissions(int [] averageElectricBill, int [] averageElecPrice){
        double[] electricityEmissions = new double[5];
        for(int counter = 0; counter <= 5; counter++){
             electricityEmissions[counter] = (averageElectricBill[counter]/averageElecPrice[counter]) * 1.37 * 12;
                }
                return electricityEmissions;
            }


    public double[] calcWasteReduction(int [] lightsTotal){
        double[] emissionReductions = new double[5];
        for(int counter = 0; counter <=5; counter++){
            emissionReductions[counter] = lightsTotal[counter] * 1.37 * 73;
        }
        return  emissionReductions;
}
    
       
       
       public double[] calcGrossWasteEmission(int [] numberOfPeople) {
            double[] grossWasteEmission = new double[5];
            for(int counter = 0; counter <=5; counter++){
                grossWasteEmission[counter] = numberOfPeople[counter] * 1018;
    }
        return grossWasteEmission;
    
}

       
    public double[] calcCanReductions(boolean [] cans,int [] numberOfPeople) {
           
               
        double [] canReductions = new double[5];
        double can = 165.8;
        for (int counter = 0; counter<=5; counter++){
                if (cans[counter]){
                canReductions [counter] = (can * numberOfPeople[counter]);
                   }
                   
                }
                return canReductions;
            }
        
            
            public double[] calcGlassReductions(boolean [] glass,int [] numberOfPeople) {
                
               double[] glassReductions = new double[5];
               double glassReduce = 46.6;
            for (int counter = 0; counter<=5; counter++){
                if(glass[counter]){
           glassReductions[counter] = (glassReduce * numberOfPeople[counter]);
                }
                
            }
            return glassReductions;
        }
            
             public double[] calcPlasticReductions(boolean [] plastic,int [] numberOfPeople) {   
             double [] plasticReductions = new double[5];
             double plasticReduce = 25.6;
            
             for (int counter = 0; counter<=5; counter++){
                  if(plastic[counter]){
              plasticReductions[counter] = (plasticReduce * numberOfPeople[counter]);
                }
                
            }
            return plasticReductions;
        }
            
           public double[] calcPaperReductions(int [] numberOfPeople, boolean [] paper) {   
               double paperReduce = 184.0;
               double [] paperReductions = new double[5];
              
            for (int counter = 0; counter<=5; counter++){
                 if(paper[counter]){
             paperReductions[counter] = (paperReduce * numberOfPeople[counter]);
                }
                
            }
        
        return paperReductions;
        
        
        
        }
        
         public double[] calcEmissionReductionTotals(double [] paperReductions, double [] plasticReductions, double[] glassReductions,double [] canReductions) {   
             double[] emissionReductionTotal = new double[5];
             for (int counter =0; counter<=5; counter++){
                 emissionReductionTotal[counter] = paperReductions[counter] + plasticReductions[counter] + glassReductions[counter] + canReductions[counter];
                }
                return emissionReductionTotal;
            }

        
        
}
```

this is mainly the part i am having trouble getting right. its not laziness i promise its just that my instructor is bad and i have gotten as far as i actually know how. 

```
public class CO2FootPrintTester
{
        public static void main(String[] args){
            
        CO2Footprint footprint = new CO2Footprint();
        
        //declaration of variables 
        
       int [] numberOfPeople =  new int[5];;
       numberOfPeople[0] = 3;
       numberOfPeople[1] = 6;
       numberOfPeople[2] = 2;
       numberOfPeople[3] = 10;
       numberOfPeople[4] = 1;
       
       double [] avgElecBill = new double [5];;
       avgElecBill[0] = 227.29;
       avgElecBill[1] = 213.28;
       avgElecBill[2] = 234.78;
       avgElecBill[3] = 256.04;
       avgElecBill[4] = 221.96;
       
       for (int counter = 0; counter <=5; counter++){
           int totalAverageElectricBill = 0;
           totalAverageElectricBill += avgElecBill [counter];
           int  averageElectricBill  = totalAverageElectricBill / 5;
        }
           
       
       boolean [] cans = new boolean[5];;
       cans[0] = true;
       cans[1] = false;
       cans[2] = true;
       cans[3] = false;
       cans[4] = true;
       
       boolean [] glass = new  boolean[5];;
       glass[0] = true;
       glass[1] = false;
       glass[2] = true;
       glass[3] = false;
       glass[4] = true;
       
       boolean [] plastic = new boolean[5];;
       plastic[0] = true;
       plastic[1] = true;
       plastic[2] = false;
       plastic[3] = false;
       plastic[4] = true;
       
       boolean [] paper  = new boolean[5];;
       paper[0] = true;
       paper[1] = false;
       paper[2] = true;
       paper[3] = false;
       paper[4] = true;
       
       int [] numLights = new int[5];;
       numLights[0] = 9;
       numLights[1] = 3;
       numLights[2] = 5;
       numLights[3] = 1;
       numLights[4] = 8;
       
       for (int counter = 0; counter<=5; counter++){
           int []  lightsTotal;
           lightsTotal[counter] += numLights[counter];
        }
       
       
       int [] gas = new int[5];;
       gas[0] = 2604;
       gas[1] = 3029;
       gas[2] = 1745;
       gas[3] = 3590; 
       gas[4] = 1362;
       
       for (int counter = 0; counter<=5; counter++){
           int gasTotal = 0;
           gasTotal += gas[counter];
        }
       
       double [] avgElecPrice = new double[5];
       avgElecPrice[0] =  .084;
       avgElecPrice[1] = .081;
       avgElecPrice[2] = .085;
       avgElecPrice[3] = .084; 
       avgElecPrice[4] = .086; 
       
       for (int counter = 0; counter <=5; counter++){
           int totalAverageElectricPrice = 0;
           totalAverageElectricPrice += avgElecPrice[counter];
           int averageElecPrice = 0;
           averageElecPrice = totalAverageElectricPrice / 5;
        }
       
      
         
        
        //call methods
        

        
        double[] gasFootprint = new double[5];
        gasFootprint = footprint.calcGlassReductions();(gas);
        double[] electricityEmissions = new double[5];
        electricityEmissions= CO2Footprint.calculateElectricityEmissions(averageElectricBill, averageElecPrice);
        double[] emissionReductions = new double[5];
        emissionReductions=  CO2Footprint.calcNetWasteReduction(cans,plastic,glass,paper, grossWasteEmission,numberOfPeople);
        double[] grossWasteEmission = new double[5];
        grossWasteEmission= CO2Footprint.calcGrossWasteEmission(numberOfPeople);
    

        
        //print results
        
        System.out.println("|               Pounds of CO2             |      Pounds of CO2         |                       |");
        System.out.println("|               Emmited from              |      Reduced from          |                       |");
        System.out.println("|   Gas   |      Electricity  |   Waste   |   Recycling  |  New Bulbs  |    CO2 Footprint      |");
    
       
    }
}

```

i just have a rough outline of the print, which is unimportant. its mostly getting this to have 5 objects, and work is my problem. any help is greatly appreciated. thanks alot ubuntu friends.

---

### Post by dwhitney67 on 2009-11-05
In a nutshell, OOP is about defining an object and the actions and attributes associated with the object.

Your main() function should look something like:
```

public static void main(String[] args)
{
   CO2Footprint fp1 = new CO2Footprint(arg1, arg2, ..., argN);
   CO2Footprint fp2 = new CO2Footprint(arg1, arg2, ..., argN);
   ...
   CO2Footprint fpN = new CO2Footprint(arg1, arg2, ..., argN);

   System.out.println("Total CO2 Footprint of Household 1: " + fp1.calcTotalFootprint());
   System.out.println("Total CO2 Footprint of Household 2: " + fp2.calcTotalFootprint());
   ...
   System.out.println("Total CO2 Footprint of Household N: " + fpN.calcTotalFootprint());
}

```
It's that simple... so to speak.  You can place the object construction in a loop, polling the user for data input.  Use your imagination.  Your assignment asks that you create at least 5 distinct CO2Footprint objects.

Your CO2Footprint class needs a constructor that accepts the parameters as indicated in your assignment.  Then you need to implement the methods that compute the CO2 footprint (for each attribute).  These methods do *not* need to be public (they could be defined as private), however you will need a public method to obtain the total CO2 footprint (eg. calcTotalFootprint()).

Re-factor your class so that it accounts for your project requirements, then post back here if you still have issues.

---

### Post by nathang1392 on 2009-11-05
alright, sorry for my incompetence. i have somewhat done what i think you suggested. with this: ```
CO2Footprint fp0 = new CO2Footprint(3, 2604, 227.29, .084, true, true, true, true, 9);
        CO2Footprint fp0 = new CO2Footprint(6, 3029, 213.28, .081, false, true, false, true, 3);
        CO2Footprint fp0 = new CO2Footprint(2, 1745, 234.78, .085, true, false, true, false, 5);
        CO2Footprint fp0 = new CO2Footprint(10, 3590, 256.04, .084, false, false, false, false, 1);
        CO2Footprint fp0 = new CO2Footprint(1, 1362, 221.96, .086, true, true, true, true, 8);
```
i put all of my numbers in there, which is what i think you wanted me to do. my question is now, do i erase the arrays that i have created?

---

### Post by dwhitney67 on 2009-11-05
> **nathang1392 said:**
> ...
i put all of my numbers in there, which is what i think you wanted me to do. my question is now, do i erase the arrays that i have created?

Do you need the arrays?

As for the constructor data, you can hard-code these (as you have shown), acquire them via user input, or perhaps read them from a file.  If the assignment's requirements don't specify how or where you are supposed to get the data, then do whatever you want.  For now, what you have is fine; I would gather that the main point of the assignment is to develop the CO2Footprint class, and not dwell so much on how/where the data comes from.

P.S.  You do not want to declare 5 fp0 variables; I think you meant fp0, fp1, ..., fp4.  Feel free to declare these as an array.
```

CO2Footprint[] fp = new CO2Footprint[5];   // sorry if this syntax is wrong; my Java is rusty.

fp[0] = new CO2Footprint(params...);
fp[1] = new CO2Footprint(params...);
...

```

---

### Post by nathang1392 on 2009-11-05
making them all 0 was actually a typo. i copied and pasted so thats what i get. yea im going to do hard coded. my question is though how do i deal with the individual parts of this? for example how do i make these objects interact with my methods( which i actully got to compile =)) to get my calculations? well im not sure if thats what im supposed to be doing. is that all those objects have to do is be declared at the top?

---

### Post by nathang1392 on 2009-11-05
also i am now getting the error cannot find symbol constructor CO2Footprint(int int double double boolean boolean boolean int) on the first line of this ```
        CO2Footprint fp0 = new CO2Footprint(3, 2604, 227.29, .084, true, true, true, true, 9);
        CO2Footprint fp1 = new CO2Footprint(6, 3029, 213.28, .081, false, true, false, true, 3);
        CO2Footprint fp2 = new CO2Footprint(2, 1745, 234.78, .085, true, false, true, false, 5);
        CO2Footprint fp3 = new CO2Footprint(10, 3590, 256.04, .084, false, false, false, false, 1);
        CO2Footprint fp4 = new CO2Footprint(1, 1362, 221.96, .086, true, true, true, true, 8);
```

---

### Post by dwhitney67 on 2009-11-05
> **dwhitney67 said:**
> ...
Your CO2Footprint class needs a constructor that accepts the parameters as indicated in your assignment...

Perhaps you glossed over the statement above when you read my post earlier.

---

### Post by nathang1392 on 2009-11-05
okay i have been looking back at your post and thinking. i looked at your examples of how to call the method, and i have a question. if i have 5 objects like so for example: 
```
CO2Footprint fp0 = new CO2Footprint(3, 2604, 227.29, .084, true, true, true, true, 9);
        CO2Footprint fp1 = new CO2Footprint(6, 3029, 213.28, .081, false, true, false, true, 3);
        CO2Footprint fp2 = new CO2Footprint(2, 1745, 234.78, .085, true, false, true, false, 5);
        CO2Footprint fp3 = new CO2Footprint(10, 3590, 256.04, .084, false, false, false, false, 1);
        CO2Footprint fp4 = new CO2Footprint(1, 1362, 221.96, .086, true, true, true, true, 8);
```

my question is though, since i have about 7 methods, would i need to make a method for each object? sorry for all of the questions im just trying to figure this out so i can get it to work.

also i have made my 

> CO2FootPrintTester(){
            
            
            }
but im not sure if this is right. i know this is like a default. do i need to put all my arrays into it?

---

### Post by nathang1392 on 2009-11-05
as of now this is my best attempt at the constructor
```
 CO2FootPrintTester(int [] numberOfPeople, double [] avgElecBill,boolean [] cans,boolean [] glass,boolean [] plastic,boolean [] paper,int [] numLights,int [] gas,double [] avgElecPrice)
            {
                
            }
```

i keep trying different things and i try to post so if im close someone can help.i got that from an example and applied it to myself. i get an error that says .class needed. im going kind of crazy#-o#-o#-o

---

### Post by dwhitney67 on 2009-11-06
It's obvious that you have been neglecting either 1) paying attention in class, or 2) reading your textbook.

Your attempt at the constructor was almost correct.  Consider the following:
```

public CO2FootPrintTester(int familySize, double avgElecBill,boolean recycleCans, boolean recycleGlass, boolean recyclePlastic, boolean recyclePaper, int numLights, int gas, double avgElecPrice)
{
   this.familySize = familySize;
   ...                
}

```

HOWEVER...

As your assignment indicates, you must define a structure for the data (sorry I did not see this earlier)...
```

class FamilyRecyclingData
{
   public FamilyRecyclingData() {}  // define only if required

   public int     familySize;
   public double  avgElecBill;
   public boolean recycleCans;
   ...
}

class CO2Footprint
{
   private FamilyRecyclingData frd;

   public CO2Footprint(FamilyRecyclingData frd)
   {
      this.frd = frd;
   }

   public double calcTotalFootprint()
   {
      ...

      return total;
   }

   // private methods
   ...
}

class CO2FootprintTester
{
   public static void main(String[] args)
   {
      FamilyRecyclingData[] frd = new FamilyRecyclingData[5];
      CO2Footprint[] fp = new CO2Footprint[5];
      
      frd[0] = new FamilyRecyclingData();
      frd[0].familySize  = 5;
      frd[0].avgElecBill = 72.50;
      ...

      CO2Footprint fp[0](frd[0]);

      System.out.println(fp[0].calcTotalFootprint());

      // repeat for other families (reuse frd object)
   }
}

```
If I were you, I would take the family recycling stats from the user; in other words, from a loop, **prompt** the user for each data point so that you can build the individual FamilyRecyclingData objects, and then pass each of these to that CO2Footprint constructor after each "frd" has been collected, or defer this until all the data for the 5 families has been collected.

---

### Post by nathang1392 on 2009-11-06
> It's obvious that you have been neglecting either 1) paying attention in class, or 2) reading your textbook.

i wish it was that simple. i dont have an instructor, nor a class. im taking a distance learning ap computer science a course. im def wishing i hadnt chose to take it. it wouldnt be bad with some instruction, but i rely on only examples of code. thanks for the help, im going to try to adapt your examples to my code.

---

### Post by nathang1392 on 2009-11-07
i have been reading and working :p im actually making good progress, im just running into some questions that i cant really find answers to.
```

/**
 * Write a description of class CO2Footprint here.
 * 
 * @author (your name) 
 * @version (a version number or a date)
 */
public class CO2Footprint
{
        private int numPeople;
        private double electricityEmissions;
        private double gas;
        private double gasFootPrint;
        private double aveElecBill;
        private double aveElecPrice;
        private boolean paper;
        private boolean plastic;
        private boolean glass;
        private boolean cans;
        private int numLights;
        private int lightsTotal;
        private double paperReductions;
        private double plasticReductions;
        private double glassReductions;
        private double canReductions;
        private double emissionReductions;
        private double emissionReductionTotal;
        private double grossWasteEmission;

  public CO2Footprint( int numberOfPeople, double gasFootPrint, double averageElectricBill, 
  double averageElectricPrice, boolean paperRecyled, boolean plasticRecyled, boolean glassRecyled,
  boolean cansRecyled, int numLightsRecyled, double totalReductionsPaper, double totalReductionsPlastic,
  double totalReductionsGlass, double totalReductionsCans, double electricityEmissions) 
    {
        numberOfPeople = numPeople;
        gasFootPrint = gas;
        averageElectricBill = aveElecBill;
        averageElectricPrice = aveElecPrice;
        paperRecyled = paper;
        plasticRecyled = plastic;
        glassRecyled = glass;
        cansRecyled = cans;
        numLightsRecyled = numLights;
        totalReductionsPaper = paperReductions;
        totalReductionsPlastic = plasticReductions;
        totalReductionsGlass = glassReductions;
        totalReductionsCans = canReductions;
      
    } 


    public double calculateGasEmissions(){
        gasFootPrint = 19.3565 * gas;
        return gasFootPrint;
        }
            
      public double calculateElectricityEmissions(){
          electricityEmissions = (aveElecBill/aveElecPrice) * 1.37 * 12;
          return electricityEmissions;
            }


    public double calcWasteReduction(){
       emissionReductions = lightsTotal * 1.37 * 73;
       return  emissionReductions;
}
    
       public double calcGrossWasteEmission() {
            grossWasteEmission = numPeople * 1018;
            return grossWasteEmission;
    
}

       
    public double calcCanReductions() {
            double can = 165.8;
                if (cans){
                    canReductions  = (can * numPeople);
                }
                return canReductions;
            }
        
    public double calcGlassReductions() {
            double glassReduce = 46.6;
                if(glass){
                    glassReductions = (glassReduce * numPeople);
              
            }
            return glassReductions;
        }
        
            
    public double calcPlasticReductions() {   
             double plasticReduce = 25.6;
             if(plastic){
                plasticReductions = (plasticReduce * numPeople);
              }
            return plasticReductions;
        }
        
        
            
    public double calcPaperReductions() {   
               double paperReduce = 184.0;
               if(paper){
                    paperReductions = (paperReduce * numPeople);   
            }
        
        return paperReductions;
        
        }
        
    public double calcEmissionReductionTotals() {   
             emissionReductionTotal = paperReductions + plasticReductions + glassReductions + canReductions;
             return emissionReductionTotal;
            } 
}
```

i *think* i have gotten this up to par. the key word is think. im having problems with my other class though ```

/**
 * Write a description of class CO2FootPrintTester here.
 * 
 * @author (your name) 
 * @version (a version number or a date)
 */

public class CO2FootPrintTester
{
        public static void main(String[] args){
            
        
      
       
        CO2Footprint fp0 = new CO2Footprint();
         fp0.numPeople = 3;
         fp0.gas = 2604;
         fp0.aveElecBill = 227.29;
         fp0.aveElecPrice = .084;
         fp0.paper = true;
         fp0.plastic = true;
         fp0.glass = true;
         fp0.cans = true;
         fp0.numLights = 9;
        
       CO2Footprint fp1 = new CO2Footprint();
        fp1.numPeople = 6;
        fp1.gas = 3029;
        fp1.aveElecBill = 213.28;
        fp1.aveElecPrice = .081;
        fp1.paper = false;
        fp1.plastic = true;
        fp1.glass = false;
        fp1.cans = true;
        fp1.numLights = 3;
        
       CO2Footprint fp2 = new CO2Footprint();
        fp2.numPeople = 2;
        fp2.gas = 3590;
        fp2.aveElecBill = 234.78;
        fp2.aveElecPrice = .085;
        fp2.paper = true;
        fp2.plastic = false;
        fp2.glass = true;
        fp2.cans = false;
        fp2.numLights = 5;
       
        
       
       CO2Footprint fp3 = new CO2Footprint();
        fp3.numPeople = 10;
        fp3.gas = 3590;
        fp3.aveElecBill = 256.04;
        fp3.aveElecPrice = .084;
        fp3.paper = false;
        fp3.plastic = false;
        fp3.glass = false;
        fp3.cans = false;
        fp3.numLights = 1;
       
       CO2Footprint fp4 = new CO2Footprint();
        fp4.numPeople = 1;
        fp4.gas = 1362;
        fp4.aveElecBill = 221.96;
        fp4.aveElecPrice = .086;
        fp4.paper = true;
        fp4.plastic = true;
        fp4.glass = true;
        fp4.cans = true;
        fp4.numLights = 8;
        
        

    

        
        //print results
        
        System.out.println("|               Pounds of CO2             |      Pounds of CO2         |                       |");
        System.out.println("|               Emmited from              |      Reduced from          |                       |");
        System.out.println("|   Gas   |      Electricity  |   Waste   |   Recycling  |  New Bulbs  |    CO2 Footprint      |");
    
    
    }
}

```

i had a constructor but it kept giving me errors. i was told else where that i only need a constructor in my other class, so i took it out all together. im slowly getting it, but if anyone can help point out some problem or errors that you see it would be great. thanks for the help so far.

---

### Post by dwhitney67 on 2009-11-08
You have this constructor, but you are not using it.  Hmmm?
```

  public CO2Footprint( int numberOfPeople, double gasFootPrint, double averageElectricBill, 
  double averageElectricPrice, boolean paperRecyled, boolean plasticRecyled, boolean glassRecyled,
  boolean cansRecyled, int numLightsRecyled, double totalReductionsPaper, double totalReductionsPlastic,
  double totalReductionsGlass, double totalReductionsCans, double electricityEmissions) 
    {
       ...
    }

```
```

        ...
        CO2Footprint fp0 = new CO2Footprint();
         fp0.numPeople = 3;
         fp0.gas = 2604;
         fp0.aveElecBill = 227.29;
         fp0.aveElecPrice = .084;
         fp0.paper = true;
         fp0.plastic = true;
         fp0.glass = true;
         fp0.cans = true;
         fp0.numLights = 9;
         ...

```

You should be calling the constructor in your test program as such:
```

        ...
        CO2Footprint fp0 = new CO2Footprint(3, 2604, 227.29, .084, true, true, true, true, 9);

```
Notice that I stopped the parameters at the number of lights.  I think the other parameters that you have declared for your constructor (ie. totalReductionsPlastic, totalReductionsPaper, etc) are computed, thus the callee of the constructor should not be passing these.  Please correct me if I am wrong.

If I am correct, then remove those 'total' parameters from the constructor.

---


---
title: "how to write this java code with shell script??"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by tibery on 2011-10-21
all
I'm a newbie in Linux
I want to make an class as core in Object Oriented Programing, and I don't know shelll script have it or not.....


I want to write this java code with shell script
please tell me how can I write this javacode in shell script
```

import java.util.*;

class calculate{
    
    //declaration volume,wide,height,width and length
    public double volume=0, wide=0;
    public double height,width,length;


    //constructor
    calculate(double height, double width, double length){

        this.length=length;
        this.width = width;
        this.height=height;

    }
    //formula to find crossbar volume
    public double getVolume(){

        
        volume=length*width*height;
        return volume;
    }
    //formula to find crossbar wide
    public double getWide(){

            wide=(2*length)+(2*width)+(2*height);
            return wide;
    }


}


class result{

    public static void main(String[] args){
            //declaration of height,width and length in main class
            double xHeight,xWidth,xLength;
            
            Scanner input = new Scanner(System.in);
            
            //input Height
            System.out.print("Input Height Crossbar : ");
            xHeight=input.nextDouble();
            //input Width
            System.out.print("Input Width Crossbar : ");
            xWidth=input.nextDouble();
            //input Length
            System.out.print("Input Length Crossbar : ");
            xLength=input.nextDouble();

            //making object call from class calculate
            calculate cal = new calculate(xHeight,xWidth,xLength);
            //Show 
            System.out.println("Wide of Crossbar is "+cal.getWide());
            System.out.println("Volume of CrossBar is "+cal.getVolume());
            
            

        }


}




```



:confused:
please help
thanks before

---

### Post by NattyLight on 2011-10-21
Do you know Shell Script syntax? If you do it shouldnt be too hard to adapt the Java code to work on shell script.

---

### Post by tibery on 2011-10-21
I can translate this shell script to java code

this the shell script
```


#!/bin/bash
#
# Linux Shell Scripting Tutorial 1.05r3, Summer-2002
#
#

MAX_NO=0

echo -n "Enter Number between (5 to 9) : "
read MAX_NO

if ! [ $MAX_NO -ge 5 -a $MAX_NO -le 9 ] ; then
   echo "I ask to enter number between 5 and 9, Okay"
   exit 1
fi

clear

for (( i=1; i<=MAX_NO; i++ ))
do
    for (( s=MAX_NO; s>=i; s-- ))
    do
       echo -n " "
    done
    for (( j=1; j<=i;  j++ ))
    do
     echo -n " ."
    done
    echo ""
done

echo -e "\n\n\t\t\tI hope you like it my stupidity (?)"




```this the java  code but with little modification "exception handling"
```

import java.util.*;
import java.io.*;


class lin{

    public static void main(String[] args)throws Exception{
            
            int Max_NO=0;
            String o;
            boolean h=false;
            Scanner t=new Scanner(System.in);
            InputStreamReader isr = new InputStreamReader(System.in);
            BufferedReader br = new BufferedReader(isr);

            

            do{
                System.out.print("Enter Number antara (5 - 9)\t :");
                o=br.readLine();

                //exception handling
                try{

                Max_NO = Integer.parseInt(o);

                if(Max_NO>=5 && Max_NO<=9){
                    
                        h=true;
                }
    
                if(h){

                        System.out.println("Thank You....\n");

                }else{
                    System.out.println("I ask to enter number between 5 and 9, Okay!!\n");

                }



                }catch(NumberFormatException e){

                    System.out.println("Enter Number Format Not String , Okay!!\n");

                }


            }while(h==false);
                

                
                


                
            for(int i=1;i<=Max_NO;i++){

                for(int s=Max_NO;s>=i;s--){
                    
                    System.out.print(" ");

                }


                for(int j=1;j<=i;j++){

                    System.out.print(" "+i);

                }

                System.out.println();

            }

    }

}


```

the logical is not too diffrent
the diffrent just in syntax
i just need the example of class object using shell script
please show me the code:confused:

Thanks before

---

### Post by NattyLight on 2011-10-21
> **tibery said:**
> I can translate this shell script to java code

this the shell script
```


#!/bin/bash
#
# Linux Shell Scripting Tutorial 1.05r3, Summer-2002
#
# Written by Vivek G. Gite <vivek@nixcraft.com>
#
# Latest version can be found at http://www.nixcraft.com/
#

MAX_NO=0

echo -n "Enter Number between (5 to 9) : "
read MAX_NO

if ! [ $MAX_NO -ge 5 -a $MAX_NO -le 9 ] ; then
   echo "I ask to enter number between 5 and 9, Okay"
   exit 1
fi

clear

for (( i=1; i<=MAX_NO; i++ ))
do
    for (( s=MAX_NO; s>=i; s-- ))
    do
       echo -n " "
    done
    for (( j=1; j<=i;  j++ ))
    do
     echo -n " ."
    done
    echo ""
done

echo -e "\n\n\t\t\tI hope you like it my stupidity (?)"

#
# ./ch.sh: vivek-tech.com to nixcraft.com referance converted using this tool
# See the tool at http://www.nixcraft.com/uniqlinuxfeatures/tools/
#


```this the java  code but with little modification "exception handling"
```

import java.util.*;
import java.io.*;


class lin{

    public static void main(String[] args)throws Exception{
            
            int Max_NO=0;
            String o;
            boolean h=false;
            Scanner t=new Scanner(System.in);
            InputStreamReader isr = new InputStreamReader(System.in);
            BufferedReader br = new BufferedReader(isr);

            

            do{
                System.out.print("Enter Number antara (5 - 9)\t :");
                o=br.readLine();

                //exception handling
                try{

                Max_NO = Integer.parseInt(o);

                if(Max_NO>=5 && Max_NO<=9){
                    
                        h=true;
                }
    
                if(h){

                        System.out.println("Thank You....\n");

                }else{
                    System.out.println("I ask to enter number between 5 and 9, Okay!!\n");

                }



                }catch(NumberFormatException e){

                    System.out.println("Enter Number Format Not String , Okay!!\n");

                }


            }while(h==false);
                

                
                


                
            for(int i=1;i<=Max_NO;i++){

                for(int s=Max_NO;s>=i;s--){
                    
                    System.out.print(" ");

                }


                for(int j=1;j<=i;j++){

                    System.out.print(" "+i);

                }

                System.out.println();

            }

    }

}


```i just need the example of class object using shell script
please show me the code:confused:

Thanks before

I would love to help but this is really the first time Ive ever seen shell script code, plus Im not really understanding, if you can translate the above SS to java, then you should be able to translate the code that you want from Java to SS.

---

### Post by tibery on 2011-10-21
maybe you're right
but without example I don't know how to make it in SS
and I don't know , do the SS have  Object Oriented Programing method like C++ or Java etc if there is no example??
I have search in several forum, and no result..
anyway thanks bro for you attention for my problem :P

---

### Post by NattyLight on 2011-10-21
> **tibery said:**
> maybe you're right
but without example I don't know how to make it in SS
and I don't know , do the SS have  Object Oriented Programing method like C++ or Java etc if there is no example??
I have search in several forum, and no result..
anyway thanks bro for you attention for my problem :P

First of all, you sound like a student... are you? And I cant really answer your question as I have never seen SS code until you just posted that code example. Looking at the example though it looks like it is not OOP, I could be wrong on that however.

plus if you do know SS syntax, you should be able to adapt the Java code to work for SS, it sounds like you do not know SS syntax however

---

### Post by thatguruguy on 2011-10-21
The [programming sub-forum]("http://ubuntuforums.org/forumdisplay.php?f=39").

Enjoy.

---

### Post by NattyLight on 2011-10-21
> **thatguruguy said:**
> The [programming sub-forum]("http://ubuntuforums.org/forumdisplay.php?f=39").

Enjoy.

Thank you!

---


---
title: "[SOLVED] Stuck On Java"
date: 2008-01-04
forum: Programming Talk
---

### Post by madsmeg on 2008-01-04
i have been working on this code for hours, and connot for the lif of me work out why it will not work :( ```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package charityassignment;

import javax.swing.*;
import java.util.*;
import java.io.*;
import java.text.*;

/*
 * @author jon
 */

public class Database {

    int TotalEmpl = 35; 
    
    
    
   
    EmployeeInfo[] Employee = new EmployeeInfo[TotalEmpl]; 
    // creates an array with size of total number of expected employee
   
     
        
    public static void main(String[] args) {
        
        EmployeeInfo NewApp;
        int EmplOption;
        String Display;
        String[] Option = {"Add", "Remove", "Update", "View", "Quit"};
        int Count= 0;
        
        
        do{JOptionPane.showConfirmDialog(null, "Enter An Employee");
        
        
        NewApp = new EmployeeInfo();
        Count = 1;    
        }while(Count==0);
        
        do{EmplOption = JOptionPane.showOptionDialog(
                    null
                    ,"What Would You Like To Do?"
                    ,"Make A Selection"
                    ,JOptionPane.YES_NO_OPTION
                    ,JOptionPane.PLAIN_MESSAGE
                    ,null
                    ,Option
                    ,"");
        
        if(EmplOption == 0){
           NewApp = new EmployeeInfo();
        }
        
        else if(EmplOption == 3){
           
            
            for(int i = 0; i < Employee.length; i++){
                 
                
                System.out.println(NewApp.getName());
                
            }
            
        }
        
        }while(EmplOption != 4);
       
        
        
              
        }
        
        
     public Database(){
            for(int i = 0; i < Employee.length; i++){
                Employee[i] = new EmployeeInfo();
            }
                
        }
    
}

class EmployeeInfo{
    // declares variables privatly for this class
    ResearcherInfo[] RWages = new ResearcherInfo[5];
    FundraiserInfo[] FWages = new FundraiserInfo[20];
    AdminInfo[] AWages = new AdminInfo[10];
    
    private double EmplNo;
    private String EmplNoSt;
    private String Name;
    private String Address;   
    private String PhoneNo;          
    private int WageOption;
    private String[] Options = {"Fundraiser", "Administrator", "Researcher"};
    private double MonthsWage;
    private double YearsWage;
    private String EmployeeType; 
    
    public EmployeeInfo(){   
        
        
        
        EmplNoSt = JOptionPane.showInputDialog("Please Enter The Number Of The Employee");
        EmplNo = Double.parseDouble(EmplNoSt);
        
        Name = JOptionPane.showInputDialog("Please Enter The Name Of The Employee");
        
        Address = JOptionPane.showInputDialog(
                "Please Enter The Address");
        
        PhoneNo = JOptionPane.showInputDialog(
                "Please Enter The Phone Number");
        
        WageOption = JOptionPane.showOptionDialog(
                    null
                    ,"What Is The Employee?"
                    ,"Make A Selection"
                    ,JOptionPane.YES_NO_OPTION
                    ,JOptionPane.PLAIN_MESSAGE
                    ,null
                    ,Options
                    ,"");
        
        if(WageOption == 2){
            ResearcherInfo ResApp = new ResearcherInfo();
            
            MonthsWage = (ResApp.getConsultancy() + ((ResApp.getPerformance() + ResApp.getRSalary()) / 12) );
            YearsWage = (ResApp.getConsultancy() + ResApp.getPerformance() + ResApp.getRSalary());
            EmployeeType = "Researcher";
        }
        
        else if(WageOption == 1){
            AdminInfo AdmApp = new AdminInfo();
            
            MonthsWage = (AdmApp.getOverTime() + (AdmApp.getASalary() / 12));
            YearsWage = (AdmApp.getASalary() + AdmApp.getOverTime());
            EmployeeType = "Administrator";
        }
        
        else if(WageOption == 0){
            FundraiserInfo FunApp = new FundraiserInfo();
            
            MonthsWage = FunApp.getFSalary() / 12;
            YearsWage = FunApp.getFSalary();
            EmployeeType = "Fundraiser";
        }
        
    /* System.out.println(WageOption);
     * This allowed me to see the value of each number */
        
    } // all the working is done here to be called later
    
    public double getEmplNo()
        {
            return EmplNo;
        }
    
    public String getName()
        {
            return Name;
        }
   
    public String getAddress()
        {
            return Address;
        }
  
    public String getPhoneNo()
        {
            return PhoneNo;
        }
    
    public double getYearsWage()
        {
            return YearsWage;
        }
    
    public double getMonthsWage()
        {
            return MonthsWage;
        }
    
    public String getEmployeeType()
        {
            return EmployeeType;
        }
}





class ResearcherInfo{
    private double RSalary;
    private double Consultancy;
    private String SPerformance;
    private double Performance;
    private String SConsultancy;
    
   
    public ResearcherInfo(){
    
        

        RSalary = 20000;
        SConsultancy = JOptionPane.showInputDialog("Please Enter The Number of Consultancy Hours For This Employee");
        Consultancy = (Double.parseDouble(SConsultancy)) * 20;
        SPerformance = JOptionPane.showInputDialog("Please Enter The Performance Pay Rate For This Employee");
        Performance = Double.parseDouble(SPerformance);
    }
    
    public double getRSalary()
        {
            return RSalary;
        }
    
    public double getConsultancy()
        {
            return Consultancy;
        }
    
    public double getPerformance()
        {
            return Performance;
        }
}



class AdminInfo{
    private double ASalary;
    private double OverTime;
    private String SOverTime;
    
    public AdminInfo(){
        
        ASalary = 17000;
        SOverTime = JOptionPane.showInputDialog("Please Enter The Number of Over-Time Hours For This Employee");
        OverTime = (Double.parseDouble(SOverTime)) * 20;
        
    }
    
    public double getASalary(){
        return ASalary;
    }
    
    public double getOverTime(){
        return OverTime;
    }
    
}

class FundraiserInfo{
    private double FSalary;
    
    public FundraiserInfo(){
        
        FSalary = 15000;
    }
    
    public double getFSalary(){
        return FSalary;
    }
    
}
```

please please please can someone help me :( The code is nowhere near finnished in what i want it to do, it just will not call Employee.length without pulling up an error

```
init:
deps-jar:
Compiling 2 source files to #####
 non-static variable Employee cannot be referenced from a static context
            for(int i = 0; i < Employee.length; i++){
1 error
BUILD FAILED (total time: 0 seconds)
```

---

### Post by Peyton on 2008-01-04
You're trying to treat a non-static variable in the same way as a static variable. In your main method, create an instance of Database and then work with that:
[PHP]public static void main(String[] args)
{
   Database db = new Database();
   ...(etc)...
   for (int i = 0; i < db.Employee.length; i++)
   {
      ...
   }
   ...
}[/PHP]

---

### Post by nitro_n2o on 2008-01-05
Add the static keyword to this line 

    EmployeeInfo[] Employee = new EmployeeInfo[TotalEmpl]; 

so it becomes 

static  EmployeeInfo[] Employee = new EmployeeInfo[TotalEmpl]; 

That should fix it... 

Good luck :)

---

### Post by madsmeg on 2008-01-05
Thanks Peyton, i had tried that, but thank you very much for the reply

Nitro_n2o, thanks that solved my one problem, but now i get an error in 
```
else if(EmplOption == 3){
           
            
            for(int i = 0; i < Employee.length; i++){
                 
                
                System.out.println(NewApp._Employee[i]_.getName());
                
            }
            
        }
```

It says it cannot find the variable, which is confusing me as it can see it in the previous line.

Thanks for your patience :)

EDIT:

If it helps , this is how i want the code to work in the end

```
for(int i = 0; i < Employee.length; i++)
                {
                
                    System.out.println(NewApp.Employee[i].getName() + "\t" 
                            + NewApp.Employee[i].getEmplNo() + "\t" 
                            + NewApp.Employee[i].getAddress() + "\t" 
                            + NewApp.Employee[i].getPhoneNo() + "\t" 
                            + NewApp.Employee[i].getMonthsWages() + "\t" 
                            + NewApp.Employee[i].getYearsWages() + "\t" 
                            + NewApp.Employee[i].getEmplType());
                }
```

EDIT 2:

I tried this:
```
System.out.println(Database.Employee[i].getName() + "\t" 
                            + Database.Employee[i].getEmplNo() + "\t" 
                            + Database.Employee[i].getAddress() + "\t" 
                            + Database.Employee[i].getPhoneNo() + "\t" 
                            + Database.Employee[i].getMonthsWage() + "\t" 
                            + Database.Employee[i].getYearsWage() + "\t" 
                            + Database.Employee[i].getEmployeeType() + "\n");
```

and it shows no Errors until it is called in the program

The error is : ```
Exception in thread "main" java.lang.NullPointerException
        at charityassignment.Database.main(Database.java:65)
Java Result: 1
```

---

### Post by madsmeg on 2008-01-05
[http://forum.java.sun.com/thread.jspa?messageID=10040622](http://forum.java.sun.com/thread.jspa?messageID=10040622)

I started a thread here, i will keep this open and mark it when solved

Thanks for the support

(The link is for me when i get home tbqh :p)

---

### Post by Peyton on 2008-01-05
You can't say NewApp.Employee[i].getName(), since NewApp is an EmployeeInfo object and doesn't have any field named Employee. Are you trying to print out the names of all the employees? Just use db.Employee[i].getName().

---


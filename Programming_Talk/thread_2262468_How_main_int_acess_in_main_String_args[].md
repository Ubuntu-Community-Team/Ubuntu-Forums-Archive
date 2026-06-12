---
title: "How main int acess in main String args[]"
date: 2015-01-25
forum: Programming Talk
---

### Post by vijay9 on 2015-01-25
i am trying to make simple login system for one person 
AccLogin and Psw
by user input through command line argumnet how to pass AccNo and password and check user input and with those variable values i'm trying to make some code but don't know next what i do...
---------------------------------------------------------------------------------code is here ------------------------------------------------------------------------------------
package atm.login;

import java.util.Scanner;

/**
 *
 * @author vj
 */
public class ATMLogin {

    /**
     * @param args the command line arguments
     */
    int acNo = 99999;
    int Psw = 9999;
   ATMLogin(){
       
        Scanner sc = new Scanner(System.in);
   }
  void AcssLogin()
  {
      System.out.println("Enter Your AcNo:");
      System.out.println("Entet Your Psw");
  }
    
    public static void main(int[] args) {
        // TODO code application logic here
        ATMLogin a1 = new ATMLogin();
        for(int i=0; i < args.length;i++) {
            if((a1.acNo == args[0]) && (a1.Psw == args[1])) {
                
            }
        }
         
    }
    public static void main(String args[]) {
        new ATMLogin();
        
    
    }
    
}

---

### Post by coffeecat on 2015-01-25
Not a tutorial.

*Thread moved to **Programming Talk**.*

---


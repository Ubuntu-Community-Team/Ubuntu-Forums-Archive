---
title: "Mysterious Frustrating Syntax Error: Java"
date: 2013-09-19
forum: Programming Talk
---

### Post by WP6r8PA on 2013-09-19
Using Eclipse: 
```
import java.util.Scanner;



public class CampsiteList {
    public static void p(String s) {System.out.println(s);}
    public static void main(String args[]){
        Scanner n = new Scanner(System.in);
        Campsite [] site = new Campsite[50];
        int siteNumber, party;
        String serviced, reserved, name, postalcode, liscence;
        
        System.out.println("Would you like to make a reservation?");
        if (n.nextLine() = "Yes") {
            for (int i; i < 50; i++) {
                p("Please enter your name: ");
                name = n.nextLine();
                p("Please enter your liscence number: ");
                liscence = n.nextLine();
                p("Please enter your postal code: ");
                postalcode = n.nextLine();
                p("Please enter your desired site number, 1-50: ");
                siteNumber = n.nextInt();
                p("Please enter the number of people in your party: ");
                party = n.nextInt();
                p("Please indicate whether or not you would like a serviced site: ");
[COLOR=#ff0000]                serviced = n.nextLine(); [/COLOR]
                
                [i] = new Campsite();
                site[i].setName(name);
                site[i].setLiscence(liscence);
                site[i].setPostalCode(postalcode);
                site[i].getSiteNumer(siteNumber);
                site[i].getParty(party);
                site[i].getServiced(serviced);
            }
        }    
            else if (n.nextLine = "No") {
                for (int i; i < site[i]; i++)
                System.out.println(site[i]);
            }
        
        
    }
    


}
```

Getting the error "Exception in thread "main" java.lang.Error: Unresolved compilation problem: Syntax error on token ";", Expression expected after this token at CampsiteList.main(CampsiteList1.java:24)"
I've been staring at it for an hour. I don't see what's wrong with it or what is supposed to come after it. I just want to sleep. Can anyone please shed some light on this? I'll be forever grateful.

---

### Post by Vaphell on 2013-09-19
```
[i] = new Campsite();
```
not that i know java but this looks like nonsense to me :-)

---

### Post by 1clue on 2013-09-19
[i] = new Campsite();

should be site[i] = new Campsite();

You have more errors than that.

Often you need to look in both directions from the point of the error.

---

### Post by WP6r8PA on 2013-09-19
FORGIVE ME I haven't done a Java course in over a year and I'm forgetting everything. I also see the if statements being hilariously wrong now as well. I'm so ashamed. Don't look! :oops:

---

### Post by WP6r8PA on 2013-09-19
I have another question after fixing Syntax error:
```
import java.util.Scanner;



public class CampsiteList {
	public static void p(String s) {System.out.println(s);}
	public static void main(String args[]){
		Scanner n = new Scanner(System.in);
		Campsite [] site = new Campsite[50];
		int siteNumber, party;
		String serviced, reserved, name, postalcode, liscence, reservation;
		
		System.out.println("Would you like to make a reservation?");
		reservation = n.nextLine();
		if (reservation == "Yes")
			for (int i = 0; i < 50; i++) {
			        p("Please enter your name: ");
			        name = n.nextLine();
			        p("Please enter your liscence number: ");
			        liscence = n.nextLine();
			        p("Please enter your postal code: ");
			        postalcode = n.nextLine();
			        p("Please enter your desired site number, 1-50: ");
			        siteNumber = n.nextInt();
			        p("Please enter the number of people in your party: ");
			        party = n.nextInt();
			        p("Please indicate whether or not you would like a serviced site: ");
			        serviced = n.nextLine();
			        reserved = "Reserved";
			        
			        site[i] = new Campsite(siteNumber, liscence, party, serviced, reserved, name, postalcode);
				
			}
		
		else if (reservation == "No") {
				for (int i = 0; i < 50; i++){
				System.out.println(site[i]);
			}
		
		
	}
	
	}
}
```

It terminates after asking me if I want to enter a reservation. Is there something wrong with my if statement; can I not use a string like that? I thought I remembered doing it before and having it work.

---

### Post by spjackson on 2013-09-20
```

if (reservation.equals("Yes")) {
}
else if (reservation.equals("No")) {
}

```
In Java, for objects, == compares identity not equality.

---

### Post by ofnuts on 2013-09-20
> **spjackson said:**
> ```

if (reservation.equals("Yes")) {
}
else if (reservation.equals("No")) {
}

```
In Java, for objects, == compares identity not equality.

and while you are at it, you can even use equalsIgnoreCase() to accept "YES/Yes/yes" answers (but the *IgnoreCase() methods are safe only for some European languages).

---

### Post by r-senior on 2013-09-20
If this is for real, or a prototype for something that is used by others, you will also want to spell licence/license correctly for the locale.

Note there is a difference between British and US English where US English uses license for both the verb and noun whereas British English uses licence for the noun and license for the verb.

---


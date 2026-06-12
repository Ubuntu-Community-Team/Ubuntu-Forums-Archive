---
title: "Help With C++ CODE"
date: 2011-03-25
forum: Programming Talk
---

### Post by KAISER91 on 2011-03-25
[IMG]http://oi56.tinypic.com/546emf.jpg[/IMG]



I'm really confused about how to write the above equation in code. It's basically asking to calculate the flow rate Q.


I've defined pi and g as;

const double PI = 3.14159
const double g = 9.8;




Thanks, help will be appreciated.

---

### Post by CharlesA on 2011-03-25
Is that homework?

You haven't really given us any info as to what you've done already.

---

### Post by KAISER91 on 2011-03-26
....................

---

### Post by hakermania on 2011-03-26
Please, mark the thread as solved, and, if you want, propose your solution for anyone following.

---

### Post by KAISER91 on 2011-03-26
That's my code, I don't know whether I translated the formula for Q correctly. 


> cout << "Flow Rate\n";
		cout << "Enter angle of cross section in degrees <0 to 90>: ";
		cin >> theta;
		while(theta < 0 || theta > 100)
		{cout << "You have entered an invalid number. Enter a number between 0 to 90: ";
		cin >> theta;}
		outputFile << "The angle of the cross section in degrees is " << theta << ".\n";

		cout << "Enter diameter of the cross section in metres: ";
		cin >> d;
		while (d<0)
		{cout << "Negative numbers are invalid. Enter a positive number: ";
		cin >> d;}
		outputFile << "The diameter of the cross section is " << d << " metres.\n";
		
		Dc = (d/2)*(1 - cos(theta));

		Q = ((pow(2.0,3.0/2.0)) * pow(Dc,5/2) * sqrt(g) * pow((theta - 0.5 * sin(2*theta)),3/2))/(8.0 * sqrt(pow(sin(theta)*(1-cos(theta)),5/2)));
        cout << "Flow Rate (Q) = "
		<< setprecision(4) << fixed << Q << endl;
		outputFile << "Flow Rate = " << Q << "\n";



		outputFile.close();
		cout << "Done!\n";

---

### Post by Some Penguin on 2011-03-26
Reread the man pages for the trig functions.

---

### Post by KAISER91 on 2011-03-26
> **Some Penguin said:**
> Reread the man pages for the trig functions.

I know how to use trig functions and I don't think that's why I get the wrong answer for Q. 

I think there is probably a misplaced bracket or something.

---

### Post by RobikShrestha on 2011-03-26
theta should be in radians
theta=theta*pi/180

---

### Post by KAISER91 on 2011-03-26
> **RobikShrestha said:**
> theta should be in radians
theta=theta*pi/180
Yeah, Robik, 

I have revised it to this now;


> Dc = (d/2.0)*(1.0 - cos(theta/180.0 * PI));
Q = (pow(2.0,3.0/2.0) * pow(Dc,5/2) * sqrt(g) * pow(((theta/180.0 * PI) - 0.5 * sin(2.0*theta/180.0 * PI)),3.0/2.0))/(8.0 * sqrt(pow(sin(theta/180.0 * PI)*(1-cos(theta/180.0 * PI)),5.0/2.0)));


Which gives me a closer answer, but I'm still 0.2 radians off the correct answer. 


Do you see anything else wrong with the code???

---

### Post by Some Penguin on 2011-03-26
Reread about the order of precedence of operators.

---

### Post by RobikShrestha on 2011-03-26
While calculating Q, in the denominator, you have put sin (theta) under the power of 2.5
it should be:
8*sqrt(sin(theta) * pow(1-cos(theta),5/2))

---

### Post by RobikShrestha on 2011-03-26
Instead of writing such long and complicated expressions, I would suggest writing smaller ones and combining them later.
eg: theta=theta*pi/180

pw3By2=pow((theta-xyz),1.5)
etc

---

### Post by KAISER91 on 2011-03-26
> **RobikShrestha said:**
> While calculating Q, in the denominator, you have put sin (theta) under the power of 2.5
it should be:
8*sqrt(sin(theta) * pow(1-cos(theta),5/2))
Ahhhhhhhhh, silly me. 

Thanks for the help, appreciate it.

---

### Post by Jonas thomas on 2011-03-27
What doe's that formula represent? From you input statements it looks like some type of fluid dynamics calculation?

---

### Post by Arndt on 2011-03-27
> **RobikShrestha said:**
> While calculating Q, in the denominator, you have put sin (theta) under the power of 2.5
it should be:
8*sqrt(sin(theta) * pow(1-cos(theta),5/2))

And 5/2 will end up as 2, not as 2.5, which is probably the intention.

---

### Post by ramsharan065 on 2012-04-13
> **KAISER91 said:**
> Yeah, Robik, 

I have revised it to this now;





Which gives me a closer answer, but I'm still 0.2 radians off the correct answer. 


Do you see anything else wrong with the code???
you have problem in pow(Dc,**5/2**)
**5/2** is **2** but you want **2.5**  so you have to do **5.0/2** or **5/2.0** or **5.0/2.0**
anyway you have to make either 5 or 2 float

---


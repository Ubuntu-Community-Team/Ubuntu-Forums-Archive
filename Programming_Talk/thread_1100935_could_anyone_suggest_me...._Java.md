---
title: "could anyone suggest me.... Java"
date: 2009-03-19
forum: Programming Talk
---

### Post by Mia_tech on 2009-03-19
guys could anyone take a look at my code (in Java) and suggest me simpler ways that I've could done as far as making the code simpler or the implementation of the classes.... I think I used too many classes for this desktop apps.... it's just a project for homework... here's what it looks like(see attachment)
Action for the "Check" button
```
public void getCompatibility() {
        //getting input from text boxes
        String name = txtfieldName.getText();
        String name1 = txtfieldName1.getText();
        int age = Integer.parseInt(txtfieldAge.getText());
        int age1 = Integer.parseInt(txtfieldAge1.getText());
        String pro = txtfieldProfession.getText();
        String pro1 = txtfieldProfession1.getText();
        double salary = Double.parseDouble(txtfieldSalary.getText());
        double salary1 = Double.parseDouble(txtfieldSalary1.getText());
        //getting imput from combo boxes
        String movie = (String) comboboxMovies.getSelectedItem();
        String movie1 = (String) comboboxMovies1.getSelectedItem();
        //getting input from radio button
        boolean sex = jRadioButtonMale.isEnabled();
        boolean sex1 = jRadioButtonMale1.isEnabled();
 
        
        //putting data into array
        Compatibility personCompatibility = new Compatibility();
        personCompatibility.addPerson(new Person(name, age, pro, salary, movie));
        personCompatibility.addPerson(new Person(name1, age1, pro1, salary1, movie1));


        //determine compatibility based on age
        personCompatibility.calcAge();
        
        //determine compatibility based on salary
        personCompatibility.calcSalary();
        
        //determine comp based on profession
        personCompatibility.calcProfession();
        
        //determine comp based on movie pick
        personCompatibility.calcMovie();
        
        txtareaOutput.setText(personCompatibility.getOutput()+personCompatibility.getScore());

        //clearing array list
        personCompatibility.emptyPerson();
        
    }
```

Class Compatibility
```
import java.util.*;
public class Compatibility {
        private int ageResult = 0;
        private String output = "";
        private int finalScore = 0;
        private double salaryDiff = 0.0;

        ArrayList<Person> p;
        //constructor
        public Compatibility()
        {
            p = new ArrayList<Person>();
        }
        public void addPerson(Person x)
        {
            p.add(x);
        }
        //give points based on age
        public String calcAge()
            {
                    if((p.get(0).getAge() >= p.get(1).getAge()) && ((ageResult = p.get(0).getAge() - p.get(1).getAge()) >= 7))
                {
                    output = "You are not compatible base on age difference"+"\n";
                }
                else if((p.get(0).getAge() <= p.get(1).getAge()) && ((ageResult = p.get(1).getAge() - p.get(0).getAge()) >= 7))
                {
                    output = "You are not compatible based on age difference"+"\n";
                }
                else
                {
                    finalScore += 2;
                    output = "You are compatible based on age difference ---> 2 points"+"\n";
                }
           return output;
        }
        //give poits based on
        public String calcProfession()
        {
                    if(p.get(0).getProfession().equals(p.get(1).getProfession()))
                {
                    finalScore += 1;
                    output += "You are compatible based on profession ---> 1 point"+"\n";
                }
                else { output += "You are not compatible based on profession"+"\n"; }
          return output;
        }
        //give points based on salary
        public String calcSalary()
        {
                    if((p.get(0).getSalary() >= p.get(1).getSalary()) && ((salaryDiff = p.get(0).getSalary() - p.get(1).getSalary()) >= 10000.0))
                {
                    output += "You are not compatible based on salary difference"+"\n";
                    
                }
                else if((p.get(0).getSalary() <= p.get(1).getSalary()) && ((salaryDiff = p.get(1).getSalary() - p.get(0).getSalary()) >= 10000.0))
                {
                    output += "You are not compatible based on salary difference"+"\n";
                    
                }
                else
                {
                    finalScore += 1;
                    output += "You are compatible based on salary ---> 1 point"+"\n";
                }
           return output;
        }
        //calc compatibility based on movies
        public String calcMovie()
        {
                    if(p.get(0).getMovie().equals(p.get(1).getMovie()))
                {
                    finalScore += 1;
                    output += "You are compatible based on movie pick ---> 1 point"+"\n";
                }
                else { output += "You are not compatible based on movie pic"+"\n"; }
            return output;
        }

        //getter
        public String getScore()
        {
            return "Your total score is "+finalScore+" out of 5";
        }
        public String getOutput()
        {
            return output;
        }
        //empty array
        public void emptyPerson()
        {
            p.clear();
        }
}

```

Class Person

```
public class Person {
    private String name = "";
    private int age = 0;
    private String profession = "";
    private double salary = 0.0;
    private String movie = "";
    //constructor
    public Person(String n, int a, String pro, double s, String m)
    {
        name = n;
        age = a;
        profession = pro;
        salary = s;
        movie = m;
    }
    //getters
    public String getName()
    {
        return name;
    }
    public int getAge()
    {
        return age;
    }
    public String getProfession()
    {
        return profession;
    }
    public double getSalary()
    {
        return salary;
    }
    public String getMovie()
    {
        return movie;
    }
}
```

---

### Post by jimi_hendrix on 2009-03-19
i havnt checked out all the code, but whats wrong with too many classes?

---

### Post by Mia_tech on 2009-03-19
> **jimi_hendrix said:**
> i havnt checked out all the code, but whats wrong with too many classes?

nothing wrong, I was just wondering if anyone could see with less classes without augmenting the coupling between them.

---

### Post by simeon87 on 2009-03-19
[LIST]
[*]Your calc___ methods return a value but this value is not used; you're using the output class variable for storing.
[*]You're using an ArrayList for Persons in Compatibility but the list will never contain more than two items. You could keep it if you want to extend it later (for more Persons) but otherwise, an array or simply two class variables would work too.
[/LIST]

> **jimi_hendrix said:**
> i havnt checked out all the code, but whats wrong with too many classes?

Too many classes means things that belong together are separated. That's not a good thing because when something changes, you'll likely need to update multiple classes.

---

### Post by Mia_tech on 2009-03-19
> **simeon87 said:**
> [LIST]
[*]Your calc___ methods return a value but this value is not used; you're using the output class variable for storing.
you're right I guess I can change those methods to "void"...
> [*]You're using an ArrayList for Persons in Compatibility but the list will never contain more than two items. You could keep it if you want to extend it later (for more Persons) but otherwise, an array or simply two class variables would work too.
[/LIST]
right, I thought of that too, but if I made only one class "Person" then I'll be putting methods in Person that really don't belong there, like: calcMovie, calcProfession, calcSalary...

> Too many classes means things that belong together are separated. That's not a good thing because when something changes, you'll likely need to update multiple classes.

---

### Post by myrtle1908 on 2009-03-20
Minor point but it is good practice to use the this keyword when referring to the current class instance.  For example, it is more Java'ish to say:-

[PHP]
public class Person {
  public Person(String name) {
    this.name = name;
  }
  private String name = "";
}[/PHP]

As an aside, I think you have done a pretty good job with your GUI.  Well done!

---


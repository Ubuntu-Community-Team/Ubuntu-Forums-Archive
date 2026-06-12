---
title: "DB design question"
date: 2012-11-02
forum: Programming Talk
---

### Post by chipppy on 2012-11-02
Good Morning

Link to previous journey post [click here]("http://ubuntuforums.org/showthread.php?t=2074752&page=2")
I am trying to design an application that uses a SQL database, Java via Java EE.  I have never worked with Databases before.
Do I design the Database first, last, or as I go?
Also do I build the database at the same stage of coding (eg design last, code last)

Sounds like a strange question.
To better explain.  When I normal build my silly little kids games, my designing go something like
Animate Image
Get images from Array
Do animation
I don’t worry about the actual array design until I actually get into the coding phase.  
A database is a different (and unknown to me anyway) beast.  This is why I ask when do I design the database.

Cheers 
Chipppy

---

### Post by KdotJ on 2012-11-02
I think it would be a good idea to have a think about what data you are going to store in the database. From this you can start thinking about the database design. Doing this well can actually save you a lot of Java code and handle data integrity for you.

If it was me, I would do the db first. But it's common to have to change the database structure as you develop your application.

But it really does depend on what you're putting in there and what role it plays in the app.

---

### Post by oldfred on 2012-11-03
Your database will be different than the spreadsheets. Where in a spreadsheet you have a customer name listed many times possibly with spelling errors so they are not all correct. In a data base the customer info is only in one place usually a separate customer table. And that may not be just one table, but you can overdo normalization.

[http://en.wikipedia.org/wiki/Database_normalization](http://en.wikipedia.org/wiki/Database_normalization)

[http://en.wikipedia.org/wiki/Codd%27s_12_rules](http://en.wikipedia.org/wiki/Codd%27s_12_rules)

[http://stackoverflow.com/questions/41233/java-and-sqlite](http://stackoverflow.com/questions/41233/java-and-sqlite)

I might start with one of your smaller spreadsheets and import it directly into a sql table. Learn a few sql commands and start reviewing fields with the same data and if that data should or should not be in a separate table.

I use sqliteman or sqlite database browser. You can export spreadsheet to a text, comma separated file and import directly. 

Learning about databases is a project all its own, if you have not used them.

---

### Post by chipppy on 2012-11-03
Good Morning

Thanks for the replies.
Lots more reading and a some thinking.
In this reply I am asking for assistance to check if my thinking (understanding) is correct or needs some correcting.

From what I can work out, I need to complete basic design of the application to the point where I have identified groups of data itmes that I would need to call from the DB (eg address of someone/something).  This gives me a broad list of things to be put into tables within the DB.

I then need to take the groups and break then down into individual variables (en Address comprises of streetName, streetNumber, suburb, postcode, etc). These logical groups become the tables.

Once I am happy that I have all the variables listed, and grouped into tables, I then go through and try to normalise the whole lot.  I need to get to 3Nf for good design but I should aim for better if I can achieve.

If this is correct then my DB design take place between basic design and detailed desgin.

Is my thinking correct or do you think I have misunderstood something?

Cheers
chipppy

---

### Post by KdotJ on 2012-11-03
Seems like you have done soon good reading. 

One thing I would personally suggest (others might disagree), but if it's something simple, don't over engineer it. What I mean by this is, if the database is simply just going to store addresses then this could be just one table and there's no need to go to 3NF. 

There is a trade-off between normalization and performance. But as I said... it depends on what the database is going to store.

---

### Post by dazman19 on 2012-11-04
3rd Normal Form is pretty good to be aiming for.

If you think you will build on top and add more features later on then you can go deeper. But its usually not necessary.

What you will probably find by doing this project is by the end of it, you will know all these things you would do better/differently next time around. But that is the nature of learning.

Good luck.

Remember you can over-normalize so don't get too strung up on it. 

If you are experienced with Java then create DAO's (Data Access Objects). Use these to manage the inserts/updates/deletes with the database. And then extend these using inheritance. It will save you an awful lot of time and wont be too difficult.

I would make an abstract class like this 
```
abstract class DbItem {

       private int _id;
       
       private int _createdat;//dont have to use unix timestamps here, but they are easy to work with. you can use date objects.
       private int _createdby;//userID.
       private int _modifiedat;//dont have to use unix timestamps here, but they are easy to work with. you can use date objects.
       private int _modifiedby; //userID
       
       public void DbItem(int id, Object data)
       {
            this.loadDefaults();
        /* construct method where anything with an ID of 0 is new, and anything with an ID > 0 i do a select to construct that out of the DB and load up the data. */
       }

    public int save()
    {
        //save method goes here. (where you return the ID from the Auto Incriment in the db.
        return 0;
    }
    public boolean isNew()
    {
        return this._id==0;
    }

    protected void loadDefaults()
    {
       //set up these bad boys:
       //  this._createdat
       // this._createdby;
       // this._modifiedat;
       // this._modifiedby;
    }

    public boolean destroy()
    {
        //delete method goes here.
        return false;
    }


} 

```

Anyways that is how i would approach it. Depends on the db you are using. But its much easier to set this up and use this than having rogue lines of "INSERT INTO x (a,b,c,d,e,f,g) VALUES ('xfd'. ...... 
All over the system.

you get the idea.

---

### Post by r-senior on 2012-11-05
If you are using Java EE, i.e. EJB3/JPA for persistence, don't design a database. Design a domain model.

In other words think about the *objects* you need in Java, add the annotations for relationships and let EJB3/JPA work out the database design in terms of tables, columns and foreign keys. You can always tweak it later for performance.

So if you had the classic employee department relationship (this is untested and parts are missing, e.g. setter methods, equals, hashCode):

*Employee.java*
```

@Entity
public class Employee {

private long id;
private String name;
...
private Department department;

@Id
@GeneratedValue(strategy=GenerationType.AUTO) 
public long getId() {
    return id;
}

public long getName() {
    return Name;
}

[COLOR="Blue"]@ManyToOne(optional=false)
public Department getDepartment() {
    return department;
}[/COLOR]

...

```

*Department.java*
```

@Entity
public class Department {

private long id;
private String name;
private Set<Employee> employees = new HashSet<>();

@Id
@GeneratedValue(strategy=GenerationType.AUTO) 
public long getId() {
    return id;
}

public long getName() {
    return name;
}

[COLOR="Blue"]@OneToMany(mappedBy="department")[/COLOR]
public Set<Employee> getEmployees() {
    return employees;
}

...

```

The beauty of designing the domain model is that you work with the Java objects (including inheritance) and JPA does the right thing (well, most of the time anyway). It's more fluid than creating a database and trying to map your domain model to it.

You'd configure the JPA persistence unit so that it auto-generates the database (this example is for the Apache Derby instance that comes embedded in Glassfish and it's OK to play around with):

*persistence.xml*
```

<?xml version="1.0" encoding="UTF-8" ?>
<persistence xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://java.sun.com/xml/ns/persistence http://java.sun.com/xml/ns/persistence/persistence_2_0.xsd"
  version="2.0" xmlns="http://java.sun.com/xml/ns/persistence">
<persistence-unit name="MyApplication" transaction-type="JTA">
    <provider>org.eclipse.persistence.jpa.PersistenceProvider</provider>
    <jta-data-source>jdbc/__default</jta-data-source>
    <class>com.mycompany.Employee</class>
    <class>com.mycompany.Department</class>
    <properties>
        <property name="eclipselink.logging.level" value="CONFIG"/>
        <property name="eclipselink.ddl-generation" value="create-tables"/>
        <property name="eclipselink.ddl-generation.output-mode" value="database"/>
        [COLOR="Red"]<property name="eclipselink.ddl-generation" value="drop-and-create-tables"/>
        <property name="eclipselink.ddl-generation.output-mode" value="database"/>[/COLOR]
    </properties>
</persistence-unit>
</persistence>

```

DAOs are a well-established pattern for Java and databases but with JPA they almost become redundant. You can have a stateless session EJB that uses a JPA entity manager which behaves like a generic DAO. Something like:

*EmployeeServiceBean.java*
```

@Stateless
public class EmployeeServiceBean implements EmployeeService {

   [B] @PersistenceContext(unitName="Sales")
    EntityManager em;[/B]
	
    @TransactionAttribute(TransactionAttributeType.REQUIRED)
    public Employee createEmployee(String name, Department department) {
        Employee employee = new Employee();
        employee.name = name;
        employee.department = department
       ** em.persist(employee);**
        return employee;
    }

    ...

```

Then you can inject your service bean into web service and web applications, e.g. this is a servlet that takes a name and department id submitted from an HTML form and creates an employee. You'd handle data types and validation better than this and you'd probably use JSF rather than servlets:

```

public class MyServlet extends HttpServlet {

   ** @EJB EmployeeService employeeService;**

    public String doPost(HttpServletRequest req, HttServletResponse res) {
        String name = request.getParameter("name");
        String dept = request.getParameter("departmentId");
        Department department = employeeService.findDepartment(dept);
        **employeeService.createEmployee(name, department);**
        ...
        // Create response here ...
    }

    ...


```

Part of the reason Java EE is so powerful (and such an monster to start with) is what happens with that createEmployee method. It manages the creation of a new employee, auto-generates the primary key and establishes the link to the department. All in the scope of a transaction such that if any part of it fails, it all fails.

If you wanted to get fancy, you could have employee as a subclass of Person so that Person works for Customer, etc. The Java EE tutorial has a good section on mapping inheritance.

And yes, I know it's a lot to learn but that's a large part of the Java EE stack in one post. :P

---


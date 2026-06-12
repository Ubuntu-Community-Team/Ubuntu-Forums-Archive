---
title: "Help with polymorphism Java."
date: 2008-04-07
forum: Programming Talk
---

### Post by vampiric_blade on 2008-04-07
Hello.

I'm having trouble getting a firm grasp on polymorphism in java.  I understand the reasoning behind overriding and overloading methods, but I still don't see the point of interfaces.  I am also confused as to when to use "extends" or "implements" in classes. 

The web has been an invaluable resource with things in java I've struggled with so far, but I just don't get that "I completely understand it now" feeling when I read about polymorphism.   Does anyone have any links to any  good, simply explained tutorials with examples?   Does anyone here feel up to the task of helping a fellow ubuntu user get a grip on polymorphism by providing any code examples of polymorphism in action?

Thank you to any helpers.

---

### Post by nick_h on 2008-04-07
Java does not support multiple inheritance.  This is why Java has the concept if an interface.  A class can only extend one parent class but can also implement multiple interfaces.  Interfaces are just like templates for classes without the methods actually being implemented.

I suggest you Google for "java multiple inheritance".

---

### Post by Ramses de Norre on 2008-04-08
You asked an example, this is an interface from an application I wrote with a database back-end. The purpose is to allow the user to use any database system he wants, he just needs to write a class that implements this interface and that class has all the database-specific code in it (an object from such a class is called a DAO, a Database Access Object). All other classes from the application use only methods defined in this interface.

The polymorphisms come into play when you define a class that uses such DAO objects, all such objects will be declared as **AbstractChiroDAO dao;** but they will be instantiated as an object from a class implementing the interface.

Making this class an interface is quite logical because:

* The methods can't be implemented;
* It would be really crappy if one coudn't subclass an existing DAO class.

I hope this gives you some insights.

```
package db;
        
/**
 * Interface to define which methods a ChiroDAO should implement.
 * @author Ramses de Norre
 *
 * <br /><p>Copyright (c) 2007, Ramses de Norre</p>
 * <p>All rights reserved.</p>
 * <p>Redistribution and use in source and binary forms, with or without modification,
 *         are permitted provided that the following conditions are met:</p>
 *
 * <p><ul>
 *         <li>Redistributions of source code must retain the above copyright notice,
 *             this list of conditions and the following disclaimer.</li>
 *         <li>Redistributions in binary form must reproduce the above copyright notice,
 *             this list of conditions and the following disclaimer in the documentation and/or
 *             other materials provided with the distribution.</li>
 *         <li>The names of its contributors may not be used to endorse or promote products derived
 *             from this software without specific prior written permission.</li>
 * </ul></p>
 * <p>
 * THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
 * "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
 * LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
 * A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR
 * CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL,
 * EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
 * PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR
 * PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF
 * LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING
 * NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
 * SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
 * </p>
 */
public abstract interface AbstractChiroDAO
{
    /**
     * Add this member to the database.
     * @param    member
     *             the member to add.
     * @throws    DAOException [must]
     *             the database has been shut down.
     */
    public abstract void add(Member member) throws DAOException;

    /**
     * Export the database to a java.io.OutputStream.
     * If you write the OutputStream to a file and give it the extension .xls,
     * then the file should be a legal excel file which represents the database.
     * @throws    DAOException [must]
     *             the database has been shut down.
     */
    public abstract void exportXLS(java.io.OutputStream out)
        throws DAOException;

    /**
     * Write all data to the database and save the database to a file (flushes the database).
     * After this method is executed all access to the database should be denied
     * and cleanly exiting the application should be guaranteed.
     * Invoking this method on a DAO whose database has already been shut down does
     * nothing but returning false.
     * @return    true if the database is successfully shut down, false in case an error
     *             occurred or the database was already shut down.
     */
    public abstract boolean shutdown();

    /**
     * This method saves all data to the database and saves the database to a file.
     * If the database was already shut down or an IOException occurred, false is returned
     * and no guarantees for the state of the database are given.
     * @return    true if the database is successfully flushed, false in case an error
     *             occurred or the database was already shut down.
     */
    public abstract boolean flush();

    /**
     * Method to check whether the database is shut down, if so you can
     * expect exceptions when trying to modify the database.
     * @return true if the database is shut down, false otherwise.
     */
    public abstract boolean isShutDown();
}

```

---

### Post by themusicwave on 2008-04-08
Ramses,

Just to clarify things I think declaring an abstract interface is a bit redundant isn't it?  

By definition all interfaces are abstract, they cannot be directly instantiated.  They can only be instantiated through one of their children.

Also, all methods in an Interface may not have a body once again by definition.  They too are always abstract so the keyword isn't needed.

While syntactically correct, I think the use of the keyword in this case is redundant and unneeded.


Is there a reason you have used the abstract keyword in your interface that I am unaware of?

The abstract keyword is quite useful when used to create an abstract class.  It allows the user to defines some common functionality that all inheriting classes will have, but still forces the inheriting class to implement certain methods.

Just wanted to clarify things a bit.

---

### Post by Ramses de Norre on 2008-04-08
> **themusicwave said:**
> Ramses,

Just to clarify things I think declaring an abstract interface is a bit redundant isn't it?  

By definition all interfaces are abstract, they cannot be directly instantiated.  They can only be instantiated through one of their children.

Also, all methods in an Interface may not have a body once again by definition.  They too are always abstract so the keyword isn't needed.

While syntactically correct, I think the use of the keyword in this case is redundant and unneeded.


Is there a reason you have used the abstract keyword in your interface that I am unaware of?

The abstract keyword is quite useful when used to create an abstract class.  It allows the user to defines some common functionality that all inheriting classes will have, but still forces the inheriting class to implement certain methods.

Just wanted to clarify things a bit.

You're right, it isn't necessary. Doesn't matter though.

---

### Post by leg on 2008-04-08
Polymorphism means change ( The capability of assuming different forms) and the meaning of the word is the clue as to what it means to you as a programmer. The example above is allowing a programmer to have the defined methods assume different forms in different situations. For instance the add method needs to act differently depending on which database is being used. Any time you override anything you are changing it and implementing polymorphism.

---


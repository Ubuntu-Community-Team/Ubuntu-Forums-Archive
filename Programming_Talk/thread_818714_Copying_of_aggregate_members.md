---
title: "Copying of aggregate members"
date: 2008-06-04
forum: Programming Talk
---

### Post by darkadept on 2008-06-04
I'm building a domain object model system in C++. I already have an O/R mapping solution based off of patterns from the book "Data Access Patterns" by Clifton Nock.
 
 My question is about copying (or cloning) my domain objects when they contain aggregate (or composite) members.
 
 For example, I have a Client domain object that stores a name, phone, and address info as strings. I have a Permit domain object that contains a Client object with the role of contractor. In my UML diagram I have this relationship defined as a 1-to-1 composite (solid diamond). So, one contractor for each Permit.
 
 When I populate my Permit object I must also populate the contractor Client object as well, right? And when I want to copy my Permit object I must make a copy of the contractor Client too, right?
 
 Now, I also have a Land domain object. The relationship between Land and Permit is a many-to-many aggregate (hollow diamonds in UML). So a Land object can be linked to many Permit objects and a Permit object can be linked to many Land objects. Permit and Land objects can exist on their own, that's why I chose aggregate instead of composite.
 
 How do I write C++ code to capture this concept? I don't have to worry too much about object destruction because I'm using a really neat reference counted smart pointer.
 
 In the Permit object do I store the Land objects as a list of pointers? If I copy a Permit object do I make a copy of every Land object? Or do I make a copy of the pointers list? If I do that I'd have two copies of a Permit object pointing to the same Land objects. 
 
 Also, I am thinking I have to use lazy initialization on these members otherwise the populate method could go into an infinite loop (populate a permit object, populate the permit's land objects, populate those land objects' permit objects, etc). Is that a sane way to look at it?
 
 I've seen a lot of Java code and some C# code but not that much C++ code written on the subject of domain objects. Any help related to this subject would be greatly appreciated!!
 
 Thanks,
 Mike

---

### Post by dwhitney67 on 2008-06-04
Can a Permit object really be valid for many Land objects?

Seems to me, and I may be wrong, that a contractor (client) would need a separate permit for each land development project.  In other words, a permit would not be valid across multiple land projects.

As for your questions, well, there were so many, and you haven't provided not even a smidgen of code.  If you need someone to write your code, then send me a PM.

Btw, can you elaborate more about the "neat reference counted smart pointer" you mentioned in your post?

Also, do you want two pointers to reference the same memory location, or do you want them to reference unique locations?  The latter would be used to deep-copy data, the former to perform a shallow-copy.

---

### Post by darkadept on 2008-06-04
Yes, in my case there can be a single Permit applied to multiple Land objects. Actually Permit is really a base class for permits like ConstructionPermit and OccupancyPermit among others.

```

class Client : public DomainObject {
public:
  Client();
  ~Client();
  void setName(const QString &name);
  QString name() const;
private:
  QString _name;
};

class Permit : public DomainObject {
public:
  Permit();
  ~Permit();
  void setContractor(const Client &contractor);
  Client contractor() const;
  void addLand(Land *land);
  QList<Land*> getLands();
private:
  Client _contractor;
  QList<Land*> _lands;
};

class Land : public DomainObject {
public:
  Land();
  ~Land();
  void addPermit(Permit *permit);
  QList<Permit*> getPermits();
private:
  QList<Permit*> _permits;
};


```

I'm really getting confused as to when I should use pointers as members or not. I know deep copying is not good unless needed and passing by reference is better then passing pointers around.

As for the smart pointer I've been using this: [http://www.ddj.com/cpp/184401243?pgno=1]("http://www.ddj.com/cpp/184401243?pgno=1"). Although I can't get the null object to work and I can't use Handle with base classes that have pure virtual methods.

I think having two pointers reference one memory location would be a bad thing to do yet deep copying is slow.

---

### Post by dwhitney67 on 2008-06-05
The smart-pointers you are referencing, although perhaps worthy, are not, IMO, worth using.  You should (IMO) use Boost's smart-pointers.

Your classes do not seem that complex at this point in time.  Thus, using some of your design, I added/embellished the code using Boost's shared-pointers (see below).

If you do not have Boost on your Ubuntu system (or Windows system), I highly recommend that you install it.  Boost can be referenced here:  [http://www.boost.org/](http://www.boost.org/)

With Ubuntu, to install (btw, I have not verified this):
```
$ sudo apt-get install boost-devel
```

Anyhow, here's the code:
[PHP]#include <boost/shared_ptr.hpp>
#include <string>
#include <list>
#include <iostream>

typedef std::string QString;


// DomainObject (???)
//
class DomainObject
{
};


// Client
//
class Client : public DomainObject
{
  public:
    Client( const QString &name )
      : _name( name )
    {
    }

    ~Client()
    {
      // nothing to do
    }

    QString name() const
    {
      return _name;
    }

    friend std::ostream & operator<<( std::ostream &os, const Client &client )
    {
      os << client._name;
      return os;
    }
  private:
    QString _name;
};


// Permit
//
class Land;

class Permit : public DomainObject
{
  public:
    typedef boost::shared_ptr< Land >  SharedLandPtr;
    typedef std::list< SharedLandPtr > Lands;


    Permit( const Client &contractor )
      : _contractor( contractor )
    {
    }

    virtual ~Permit()
    {
    }

    const Client & contractor() const
    {
      return _contractor;
    }

    void addLand(Land *land)
    {
      _lands.push_back( SharedLandPtr(land) );
    }

    const Lands & getLands() const
    {
      return _lands;
    }

    friend std::ostream & operator<<( std::ostream &os, const Permit &permit )
    {
      os << "Contractor: " << permit._contractor;
      return os;
    }

  private:
    Client _contractor;
    Lands  _lands;
};


// Land
//
class Permit;     // not really necessary, but would be if Permit defined in separate file.

class Land : public DomainObject
{
  public:
    typedef boost::shared_ptr< Permit >  SharedPermitPtr;
    typedef std::list< SharedPermitPtr > Permits;


    Land() {}

    Land( const QString & location )
      : _location( location )
    {
    }

    ~Land() {}

    void setLocation( const QString &location )
    {
      _location = location;
    }

    const QString & getLocation() const
    {
      return _location;
    }

    void addPermit( Permit *permit )
    {
      _permits.push_back( SharedPermitPtr(permit) );
    }

    const Permits & getPermits() const
    {
      return _permits;
    }

    friend std::ostream & operator<<( std::ostream &os, const Land &land )
    {
      unsigned int i = 0;

      os << "Property: " << land._location << "\n";
      for ( Permits::const_iterator it = land._permits.begin(); it != land._permits.end(); ++it )
      {
        // Dereferencing 'it' yields the Shared Pointer (SP); dereferencing the SP
        // yields the Permit object.
        //
        os << "Permit " << ++i << ": " << *(*it) << "\n";
      }
      return os;
    }

  private:
    QString _location;
    Permits _permits;
};


int main()
{
  // Create some Client objects (on the stack)
  //
  Client client_one( "Guido the Painter" );
  Client client_two( "Bubba the Plumber" );

  // Create some Permit objects (on the heap)
  //
  Permit *permit_one = new Permit( client_one );
  Permit *permit_two = new Permit( client_two );

  // Create a Land object (on the stack), and add Permit objects
  //
  Land land;

  {
    // Note, this is not necessary, but merely to show that a temp object can
    // be destroyed, yet the Shared Pointers will survive.
    //
    Land land_temp = Land( "Castle In The Sky" );
    land_temp.addPermit( permit_one );
    land_temp.addPermit( permit_two );

    // Copy temporary Land object into another
    //
    land = land_temp;

    std::cout << "Land Temp:\n" << land_temp << std::endl;

    // land_temp will be destroyed at the end of this block.
  }

  // Show results
  //
  std::cout << "Land:\n" << land << std::endl;

  const Land::Permits &permits = land.getPermits();

  std::cout << "Permits for '" << land.getLocation() << "':\n";
  for ( Land::Permits::const_iterator it = permits.begin(); it != permits.end(); ++it )
  {
    // Dereferencing 'it' yields the Shared Pointer (SP); dereferencing the SP
    // yields the Permit object.
    //
    std::cout << "\t" << *(*it) << std::endl;
  }

  return 0;
}[/PHP]

---


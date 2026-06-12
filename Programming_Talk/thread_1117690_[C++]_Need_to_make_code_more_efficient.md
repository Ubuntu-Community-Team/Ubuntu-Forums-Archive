---
title: "[C++] Need to make code more efficient"
date: 2009-04-06
forum: Programming Talk
---

### Post by dwhitney67 on 2009-04-06
I have the following, which works properly, however I wonder if it can be made more efficient, perhaps by dispensing with the vector.  Any thoughts:

```

...
typedef std::basic_string<unsigned char> RawData;
typedef std::vector<RawData>             RawDataVec;

RawDataVec rdvec;

if (m_queue.pop(rdvec, m_numReportsToSend))
{
   RawData rd;

   for (RawDataVec::const_iterator cit = rdvec.begin(); cit != rdvec.end(); ++cit)
   {
     rd += *cit;
   }

   m_sockOut.send(rd.data(), rd.size(), m_reportingAddr, m_reportingPort);
}

```

The queue is actually a circular queue.  Here's a partial listing:
```

template <typename T, size_t SIZE = 1024>
class CircularQueue
{
public:
   ...

   bool pop(std::vector<T>& elems, size_t numElemsToPop = 1)
   {
      pthread_mutex_lock(&m_mutex);

      while (m_elems > 0 && numElemsToPop--)
      {
         elems.push_back( m_buffer[ m_front ] );

         m_front = ++m_front % m_qsize;

         --m_elems;
      }

      pthread_mutex_unlock(&m_mutex);

      return !elems.empty();
   }
...
};

```

Originally I implemented pop() to use the operator+=() of the object T in lieu of bothering with a vector.  However not every object T has operator+=() defined.  It looked like:
```

template <typename T, size_t SIZE = 1024>
class CircularQueue
{
public:
   ...

   bool pop(T& elem, size_t numElemsToPop = 1)
   {
      pthread_mutex_lock(&m_mutex);

      while (m_elems > 0 && numElemsToPop--)
      {
         elem += m_buffer[ m_front ];  // operation not supported for all T, thus CircularQueue not truly generic

         m_front = ++m_front % m_qsize;

         --m_elems;
      }

      pthread_mutex_unlock(&m_mutex);

      return !elem.empty();
   }
...
};

```
When writing one-of-a-kind code, is it better to sacrifice code re-usability for the sake of efficiency?

---

### Post by Yacoby on 2009-04-06
> **dwhitney67 said:**
> When writing one-of-a-kind code, is it better to sacrifice code re-usability for the sake of efficiency?
Have you considered using Template Meta Programming and iterator_traits to check if the type T supports random access and throwing a compile time error if it doesn't? It would allow you to use more types at least.
I am fairly sure Effective C++ 3rd Edition had something on this.

Anyway, if you are worried in any way about the performance of a piece of code, imho you should run it through a profiler.

---

### Post by dwhitney67 on 2009-04-06
> **Yacoby said:**
> Have you considered using Template Meta Programming and iterator_traits to check if the type T supports random access and throwing a compile time error if it doesn't? It would allow you to use more types at least.

I am fairly sure Effective C++ 3rd Edition had something on this.

I did not need to do anything special to get a compiler error if the type T, were say, of type Foo.  If Foo does not implement operator+=(), then the compiler will complain.

P.S.  I do not have the Effective C++ book; maybe come B-day or Xmas I will add it to my list.

---


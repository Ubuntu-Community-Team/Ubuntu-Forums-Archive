---
title: "C++ discard qualifiers error"
date: 2011-11-03
forum: Programming Talk
---

### Post by erotavlas on 2011-11-03
Hi,

I have a question about the "discards qualifiers" error. I have searched a lot on the web, but I can solve only a few cases when the error appears. For example I have written a snippet of code that replicates the error on my program. 

```

class Element
{
public:

    typedef std::map<std::string, const std::vector<double>* > FunctionValuesElement;
    
    Element(const int number_of_element, const double value)
    {
        // some operation to fill the map
        std::vector<double> temp(number_of_element, value);
        function_values_element["Id_1"] = &temp;
    }

    ~Element()
    {
        // deallocate the function_values_element
    }

    const FunctionValuesElement& SetFunctionValuesElement(const FunctionValuesElement& function_values_element_)
    {
        for(FunctionValuesElement::const_iterator it = 
                function_values_element_.begin(); 
                it != function_values_element_.end(); ++it)
        {
            function_values_element[it->first] = it->second; // first error
        }
        
        
        return function_values_element;
    }

    const FunctionValuesElement& GetFunctionValuesElement() const // second error
    {       
        return function_values_element;
    }

private:

    FunctionValuesElement function_values_element;

};

```

and the error is 
```

error: passing ‘const Element::FunctionValuesElement’ as ‘this’ argument of ‘mapped_type& std::map<_Key, _Tp, _Compare, _Alloc>::operator[](const key_type&) [with _Key = std::basic_string<char>, _Tp = const std::vector<double>*, _Compare = std::less<std::basic_string<char> >, _Alloc = std::allocator<std::pair<const std::basic_string<char>, const std::vector<double>*> >, mapped_type = const std::vector<double>*, key_type = std::basic_string<char>]’ discards qualifiers

```

An other error is this
```

error: passing ‘const Elements’ as ‘this’ argument of ‘const Elements::FunctionValuesElement& Elements::GetFunctionValuesElement()’ discards qualifiers

```

I can solve the second error by removing the const keyword from the declaration of the function, but in other case the error doesn't disappear.

So I can't understand how can I solve this type of error. Any help is appreciate.

Thank you

---

### Post by GeneralZod on 2011-11-03
Compiles fine, here.  However, in Element's constructor, you are storing a pointer to a local variable which will almost surely triggered Undefined Behaviour later on.

Edit:

If you're trying to do something like 

```

e.GetFunctionValuesElement()["sausage"]';

```

this will trigger the first error, as std::map::**operator[] is non-const (you want to use std::map::find instead).

I have no idea what you're doing to get the second error, though.  The only thing I could think of to trigger it would be to declare GetFunctionValuesElement() as *non*-const and try to call it on a const Element.

Can you give us a complete program that shows the two errors?

---

### Post by erotavlas on 2011-11-04
Hi,

thank you for your fast reply. I have solved the second error. It is a due to const attribute in function declaration. I have missed it in my code...

For the first error you are right...


Thank you very much.

---


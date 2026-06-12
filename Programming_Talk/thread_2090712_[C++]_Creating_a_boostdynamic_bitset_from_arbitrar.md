---
title: "[C++] Creating a boost::dynamic_bitset from arbitrary raw data"
date: 2012-12-03
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2012-12-03
I want to know if there is more "official" or efficient way to create a dynamic_bitset from any raw data. I am not good with template code, but as far as I can tell there isn't class constructor for my use case. So I have written this piece of code:

[php]
.....
  unsigned int length(ehave->string_length());
  char const* first = ehave->string_ptr();

  boost::dynamic_bitset<> array(length*8);

  for (unsigned int i=0; i<length; i++)
  {
    char const* byte = first+i;

    for (unsigned int a=0; a<8; a++)
      array[a + i*8] = (*byte & (1<<(a)));
  }
.....[/php]

What do you think? How do you do it?

---

### Post by SledgeHammer_999 on 2012-12-03
And as I said I am not good with reading template code. After some more searching, it seems that there is a suitable constructor:

[php]template <typename BlockInputIterator>
    dynamic_bitset(BlockInputIterator first, BlockInputIterator last,
                   const Allocator& alloc = Allocator());
[/php]

So all I have to do now is:

[php]
....
  unsigned int length(ehave->string_length());
  char const* first = ehave->string_ptr();

  boost::dynamic_bitset<unsigned char> array(first, first+length);
....
[/php]

---


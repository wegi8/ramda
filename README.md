Project Ramda
=============

A practical functional library for Javascript programmers.



Goals
-----

![Ramda Logo](https://raw.github.com/CrossEye/ramda/master/logo/ramda_200x235.png)
Using this library should feel as much like using Javascript as 
possible.  Of course it's functional Javascript, but we're not 
introducting lambda expressions in strings, we're not borrowing consed 
lists, we're not porting over all of the Clojure functions.

Our basic data structures will be normal Javascript objects, and our 
usual collections will be Javascript arrays.  We will not try to reach 
the point where all the functions have only zero, one, or two arguments.  
We will certainly try to keep some of the normal features of Javascript 
that seem to be unusual in functional languages, including variable 
length function signatures and functions as objects with properties.

Functional programming is in good part about immutable objects and 
side-effect free functions.  We will stick to that as much as feasible, 
but will not be dogmatic about it.

As much as we can, we would like the implementation to be both clean and 
elegant.  But the API is king: we will sacrifice a great deal of 
implementation elegance for even a slightly cleaner API.

Unlike the developers of that silly-named _Eweda_ project, though, this 
one will focus also on performance, striving for a reliable and quick 
implementation over any notions of functional purity.



Documentation
-------------

Please review the [annotated source code 
documentation](https://rawgithub.com/CrossEye/ramda/master/docs/ramda.ht
ml) (generated by [Docco](http://jashkenas.github.io/docco/)). So far, 
that's the only documentation available.



The Name
--------

Ok, so we like sheep.  That's all.  It's a short name, not already 
taken.  It could as easily have been `eweda`, but then we would be 
forced to say _eweda lamb!_, and no one wants that.  For non-English 
speakers, lambs are baby sheep, ewes are female sheep, and rams are male 
sheep.  So perhaps ramda is a grown-up lambda... but probably not.



Structure
---------

### Automatic Currying ###

The functions included should automatically allow for partial 
application without an explicit call to lPartial.  Many of these operate 
on lists.  A single list parameter should probably come last, which 
might conflict with the design of other libraries that have strong 
functional components (I'm looking at you Underscore!)

The idea is that, if foldl has this signature:

    var foldl = function(fn, accum, arr) { /* ... */}

and we have this simple function:

    var add = function(a, b) {return a + b;};

then, instead of having to manually call lPartial like this:

     var sum = lPartial(foldl, add, 0);
     var total = sum([1, 2, 3, 4]);

with ramda, we can just do this:

     var sum = foldl(add, 0);
     var total = sum([1, 2, 3, 4]);



Functions included
-------------------

We want to include the basic functions that will help a Javscript 
programmer work with objects and arrays.  We will try to use the most 
common names for these, possibly using multiple aliases for those that 
are most debated.

### Core ###

  * isEmpty
  * isAtom
  * curry
  * prepend (cons)
  * append
  * merge
  * head (car)
  * tail (cdr)
  * size

### Functions ###

  * compose (fog)
  * pipe (sequence) (i.e., like compose but in reverse order)
  * flip
  * partial (applyLeft)
  * rPartial (applyRight)
  * memoize
  * once
  * wrap
  * nAry

### Lists ###

  * map
  * foldl (reduce)
  * foldl1
  * foldr (reduceRight)
  * foldr1
  * filter
  * reject
  * take
  * takeWhile
  * skip (drop)
  * skipUntil
  * find
  * all (every)
  * any (some)
  * contains
  * uniq
  * pluck
  * flatten
  * zip
  * zipWith
  * xprod (i.e. cartesian product)
  * xprodWith (i.e. cartesian product with function)
  * reverse
  * range
  * nth
  * indexOf
  * lastIndexOf
  * splice
  * join
  * comparator

### Generators ###

  * tail
  * take
  * skip
  * map
  * filter

### Objects ###

  * tap (K)
  * eq
  * prop
  * func
  * props
  * identity (I)
  * alwaysTrue
  * alwaysFalse
  * alwaysZero
  * maybe
  * keys
  * values
  * pick
  * invoker

### Logic ###

  * and
  * or
  * not
  * andFn
  * orFn
  * notFn

### Arithmetic ###

  * add
  * multiply
  * subtract
  * divide
  * sum
  * product

### Strings ###

  * substring
  * substringFrom
  * substringTo
  * charAt
  * charCodeAt
  * match
  * strIndexOf
  * strLastIndexOf

### Data querying ###

  * project
  * keyValue
  * sortBy
  * countBy
  * groupBy

### Miscellaneous ###

  * identity (I)
  * installTo
  * alwaysZero
  * alwaysTrue
  * alwaysFalse



So What's With Eweda?
---------------------

The [eweda library](https://github.com/CrossEye/eweda) was written by 
the developers of this library, with similar goals.  But that one strove 
more for implementation elegance than for practical capabilities.  Ramda 
is all about giving users real-world tools.  Eweda can be seen more as 
an academic excercise, mostly proving out was does and doesn't work, and 
doing so as elegantly as possible.
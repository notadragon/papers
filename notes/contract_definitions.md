Definitions
-----------

Avoided terms:

* "assume" -- as it is not clear who assumes, is it a voluntary action or a command, and what the implication of the assumption is,
* "expect" -- as it is not clear who expects and why would anyone else care what the other person or function expects; you 
  can "expect" that people will use your function incorrectly, 
* "assert" -- as "assert" could mean "trust me, I say it and this is true", or "test this hypothesis for me"
* "check" -- as it implies that some run-time checking will be performed or required, whereas some predicates are not even 
  expressible as code that could be executed.

#### *Contract annotation*

It has a *location* in code: just before the function execution begins, or just after the function execution end successfully.
It has a *predicate*, such as `p != nullptr`. Its "semantics" is: if the execution reaches the contract anntation,
and the predicate can be determined (not necessarily by evaluating it) to be `false`, then the program has a *contract violation*.
The information about a contract violation in the program
can be used in different ways by different tools, including the compiler.  

Thus, contract annotation helps provide a definition of a bug that is understandabe by machines. Becuse contract violation is for sure a manifestation of a bug.


#### *Contract violation*

A contract violation results from an interaction between the code before the contract annotation and the contact annotation 
itself. The behavior of a program with a contract violation can differ from one translation to the other based on compiler 
switches. This is similar to implementation-defined behavior except that we try to specify in more detail what the variance
in behavior is, and under what conditions.

A program with a contract violation can still be a well-formed, UB-free program. Unless other UB kicks in later on, you can
still reason about the behavior of the program in terms of operations on the abstract machine.

Contract violation is a symptom of a bug located either before the contract annotation or inside its predicate. 
Contract annotations can detect symptoms of bugs, but not bugs themselves. 
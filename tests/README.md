# Compiler Tests

To run the tests, make sure that your compiler file is called
"compiler.scm", and that at the top of that file, you have:
(load "tests-driver.scm") ; this should come first
(load "tests-1.1-req.scm") ; and any other test files you may have.

Also, make sure that your compiler defines the function
compile-program that takes an expression and uses "emit" to emit the
appropriate instructions.

The tests-driver defines the procedure "test-all" that will run all
the tests provided, get the output, redirect it to a file "stst.s",
and invokes gcc on that file as well as the runtime.c file that you
should have written.

The tests-driver is written for [Petite] Chez Scheme 7.  You can
obtain a copy of Petite Chez Scheme from: <http://www.scheme.com>

The tests-driver also assumes that you have the GNU C compiler "gcc"
already setup and added to your pathname.  How you do this depends
on your platform.  If you have a different C compiler that you wish
to use, you can edit the tests-driver yourself (look for the
definition of the build procedure).

If all is well, then invoking petite on your compiler and typing
(test-all) should run all the tests as in the following sample
transcript.

```
$ petite compiler.scm
Petite Chez Scheme Version 7.0a
Copyright (c) 1985-2005 Cadence Research Systems

> (test-all)
  test 0:#f ... ok
  test 1:#t ... ok
  test 2:() ... ok
  test 3:0 ... ok
  test 4:1 ... ok
  test 5:-1 ... ok
  test 6:2736 ... ok
  test 7:-2736 ... ok
  test 8:536870911 ... ok
  test 9:-536870912 ... ok
  test 10:#\nul ... ok
  ...
  test 131:#\y ... ok
  test 132:#\z ... ok
  test 133:#\{ ... ok
  test 134:#\| ... ok
  test 135:#\} ... ok
  test 136:#\~ ... ok
  test 137:#\rubout ... ok
  passed all 138 tests
>
```

Enjoy.

Abdulaziz Ghuloum <aghuloum@cs.indiana.edu>

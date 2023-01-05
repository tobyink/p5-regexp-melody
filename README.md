# Regexp::Melody ![linux](https://github.com/tobyink/p5-regexp-melody/workflows/linux/badge.svg)

Melody is a language that compiles to regular expressions, while aiming to be more readable and maintainable

# SYNOPSIS

```perl
use Test2::V0;
use Regexp::Melody;

my $re = Regexp::Melody->new( <<'MELODY' );
16 of "na";

2 of match {
  <space>;
  "batman";
}
MELODY

like( "nananananananananananananananana batman", $re );

done_testing;
```

# DESCRIPTION

Melody is a more verbose way of writing regular expressions.

Melody syntax is described at [https://yoav-lavi.github.io/melody/book/](https://yoav-lavi.github.io/melody/book/).

This module is a wrapper around the Rust implementation of Melody, and
provides a functional interface identical to the Rust library, as well as
an object-oriented interface which may be more convenient for use in Perl.

# FUNCTIONAL INTERFACE

No functions are exported by default, but they may be requested:

```perl
use Regexp::Melody qw( compiler );
```

## Functions

### `compiler( $melody )`

Compiles the string of Melody into a PCRE-like string.

# OBJECT-ORIENTED INTERFACE

## Constructor

### `new( $melody )`

Compiles a string of Melody into a regular expression.

The returned object is a blessed Perl object, but may be used on the right
hand side of the \`=~\` operator like a regexp.

(It's actually a blessed regexp ref, but that detail may change in future
versions of this module.)

## Methods

### `to_melody()`

Turns the regexp back into a string of Melody.

# BUGS

Please report any bugs to
[https://github.com/tobyink/p5-regexp-melody/issues](https://github.com/tobyink/p5-regexp-melody/issues).

# SEE ALSO

[https://crates.io/crates/melody\_compiler](https://crates.io/crates/melody_compiler).

[https://yoav-lavi.github.io/melody/book/](https://yoav-lavi.github.io/melody/book/).

# AUTHOR

Author: Toby Inkster

Contributors:

Yoav Lavi (Rust library)

# COPYRIGHT AND LICENSE

This software is copyright (c) 2023 by Toby Inkster.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.

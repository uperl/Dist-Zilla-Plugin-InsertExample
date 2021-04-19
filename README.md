# Dist::Zilla::Plugin::InsertExample ![linux](https://github.com/uperl/Dist-Zilla-Plugin-InsertExample/workflows/linux/badge.svg) ![macos](https://github.com/uperl/Dist-Zilla-Plugin-InsertExample/workflows/macos/badge.svg) ![windows](https://github.com/uperl/Dist-Zilla-Plugin-InsertExample/workflows/windows/badge.svg) ![cygwin](https://github.com/uperl/Dist-Zilla-Plugin-InsertExample/workflows/cygwin/badge.svg) ![msys2-mingw](https://github.com/uperl/Dist-Zilla-Plugin-InsertExample/workflows/msys2-mingw/badge.svg)

Insert example into your POD from a file

# SYNOPSIS

In your dist.ini:

```
[InsertExample]
```

In your POD:

```
=head1 EXAMPLE

Here is an exaple that writes hello world to the terminal:

# EXAMPLE: example/hello.pl
```

File in your dist named example/hello.pl

```
#!/usr/bin/perl
say 'hello world';
```

After dzil build your POD becomes:

```
=head1 EXAMPLE

Here is an example that writes hello world to the terminal:

 #!/usr/bin/perl
 say 'hello world';
```

and example/hello.pl is there too (unless you prune it with another
plugin).

# DESCRIPTION

This plugin takes examples included in your distribution and
inserts them in your POD where you have an EXAMPLE directive.
This allows you to keep a version in the distribution which
can be run by you and your users, as well as making it
available in your POD documentation, without the need for
updating example scripts in multiple places.

When the example is inserted into your pod a space will be appended
at the start of each line so that it is printed in a fixed width
font.

This plugin will first look for examples in the currently
building distribution, including generated and munged files.
If no matching filename is found, it will look in the distribution
source root.

# OPTIONS

## remove\_boiler

Remove the `#!/usr/bin/perl`, `use strict;` or `use warnings;` from
the beginning of your example before inserting them into the POD.

## indent

Specifies the number of spaces to indent by.  This is 1 by default,
because it is sufficient to force POD to consider it a verbatim
paragraph.  I understand a lot of Perl programmers out there prefer
4 spaces.  You can also set this to 0 to get no indentation at all
and it won't be a verbatim paragraph at all.

# AUTHOR

Graham Ollis <plicease@cpan.org>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2013 by Graham Ollis.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.

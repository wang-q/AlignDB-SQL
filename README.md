[![Build Status](https://travis-ci.org/wang-q/AlignDB-SQL.svg?branch=master)](https://travis-ci.org/wang-q/AlignDB-SQL)
[![codecov](https://codecov.io/gh/wang-q/AlignDB-SQL/branch/master/graph/badge.svg)](https://codecov.io/gh/wang-q/AlignDB-SQL)
[![Cpan version](https://img.shields.io/cpan/v/AlignDB-SQL.svg)](https://metacpan.org/release/AlignDB-SQL)

# NAME

AlignDB::SQL - An SQL statement generator.

# SYNOPSIS

    my $sql = AlignDB::SQL->new();
    $sql->select([ 'id', 'name', 'bucket_id', 'note_id' ]);
    $sql->from([ 'foo' ]);
    $sql->add_where('name',      'fred');
    $sql->add_where('bucket_id', { op => '!=', value => 47 });
    $sql->add_where('note_id',   \'IS NULL');
    $sql->limit(1);

    my $sth = $dbh->prepare($sql->as_sql);
    $sth->execute(@{ $sql->{bind} });
    my @values = $sth->selectrow_array();

    my $obj = SomeObject->new();
    $obj->set_columns(...);

# DESCRIPTION

_AlignDB::SQL_ represents an SQL statement.

Most codes come from Data::ObjectDriver::SQL

# ATTRIBUTES

## replace

with this, as\_sql() method will replace strings in the final SQL statement

# ACKNOWLEDGEMENTS

Sixapart

# AUTHOR

Qiang Wang &lt;wang-q@outlook.com>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2008 by Qiang Wang.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.

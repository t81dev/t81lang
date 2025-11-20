# T81Lang Grammar Specification

## Program Structure

```ebnf
program        ::= { function }*
function       ::= "fn" identifier "(" { parameter }* ")" "->" type "{" { statement }* "}"
parameter      ::= identifier ":" type
```

## Statements

```ebnf
statement      ::= assignment
                | return
                | control_flow
                | expression

assignment     ::= ("let" | "const") identifier ":" type "=" expression ";"
return         ::= "return" expression ";"
```

## Control Flow

```ebnf
if_statement   ::= "if" expression "{" { statement }* "}" [ "else" "{" { statement }* "}" ]
loop_statement ::= "for" identifier "in" expression ".." expression "{" { statement }* "}"
                | "while" expression "{" { statement }* "}"
control_flow   ::= if_statement | loop_statement
```

## Expressions

```ebnf
expression          ::= literal
                     | identifier
                     | binary_operation
                     | unary_operation
                     | function_call
                     | ternary_expression
                     | "(" expression ")"

binary_operation    ::= expression binary_operator expression
binary_operator     ::= "+" | "-" | "*" | "/" | "%" | "==" | "!=" | "<" | ">" | "<=" | ">="

unary_operation     ::= unary_operator expression
unary_operator      ::= "!" | "-"

ternary_expression  ::= expression "?" expression ":" expression

function_call       ::= identifier "(" { expression }* ")"
```

## Literals & Types

```ebnf
literal             ::= integer_literal
                     | float_literal
                     | ternary_literal
                     | string_literal

integer_literal     ::= digit+ "t81"
float_literal       ::= digit+ "." digit+ "t81"
ternary_literal     ::= digit | "+" | "-"
string_literal      ::= "\"" { char }* "\""

type                ::= "T81BigInt"
                     | "T81Float"
                     | "T81Fraction"
                     | "T81Matrix"
                     | "T81Tensor"
                     | "T81Graph"
```

## Lexical Tokens

```ebnf
identifier          ::= letter { letter | digit }*
letter              ::= "a".."z" | "A".."Z" | "_"
digit               ::= "0".."9"
char                ::= letter | digit | " " | "!" | "\"" | "#" | "$" | "%" | "&" | "'"
                     | "(" | ")" | "*" | "+" | "," | "-" | "." | "/" | ":" | ";" | "<"
                     | "=" | ">" | "?" | "@" | "[" | "\\" | "]" | "^" | "_" | "`" | "{"
                     | "|" | "}" | "~"
```

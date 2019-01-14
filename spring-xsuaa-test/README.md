# XSUAA Security Test library

This library enhances the `spring-xsuaa` project.
This includes for example a `JwtGenerator` that generates JSON Web Tokens (JWT) that can be used for JUnit tests, as well as for local testing.

 `JwtGenerator` provides these helper functions to you:
 1. load an encoded **Jwt token from file** or
 1. create a **Jwt token from a template file**, whereas some placeholders gets replaced
 1. create a **basic Jwt token** that has minimal set of preconfigured claims, **which can be enhanced** with `scopes` and `xs.user.attributes` claims and `keyId` header.
 1. create an **individual Jwt token** based on a set of claims using Nimbus JOSE + JWT [`JWTClaimsSet.Builder()`](http://www.javadoc.io/doc/com.nimbusds/nimbus-jose-jwt/6.5.1).

 All of them are returned as [`Jwt`](https://docs.spring.io/spring-security/site/docs/current/api/org/springframework/security/oauth2/jwt/Jwt.html), which offers you a `getTokenValue()` method that returns the encoded and signed Jwt token. You need to prefix this one with `Bearer ` in case you like to provide it via `Authorization` header to your application.

 > In most cases the Jwt gets Base64 encoded and signed with this [private key](/src/main/resources/privateKey.txt).

Find examples on how to use the `JwtGenerator` [here](src/test/java/com/sap/cloud/security/xsuaa/test/JwtGeneratorTest.java).
War Example
===========

Example to reproduce the problem of `provided` configurations removing all transitive
dependencies, regardless of whether the same dependencies where declared elsewhere.

See also: https://github.com/nebula-plugins/gradle-extra-configurations-plugin/issues/31


Structure
---------

    transitive
        compile 'com.google.guava:guava:20.0'
    war-with-transitive
        provided project(':transitive')
        compile 'com.google.guava:guava:20.0'
    war-with-providedCompile-transitive
        providedCompile project(':transitive')
        compile 'com.google.guava:guava:20.0'
    war-with-compileOnly-transitive
        compileOnly project(':transitive')
        compile 'com.google.guava:guava:20.0'
    war-without-transitive
        compile 'com.google.guava:guava:20.0'


When producing a war from `war-with-transitive` or `war-with-providedCompile-transitive`, 
guava is not in the resulting artifact.



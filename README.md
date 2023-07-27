# poi 漏洞修复引发的一些问题



> poi版本升级：poi 3.17-->4.1.2 

> 升级原因：poi 3.17 存在漏洞



遇到问题：jxls依赖poi，poi升级到4.1.2版本，会导致jxls1.x不兼容。

解决方案：重构 jxls1.x，适配 poi 4.1.2

方案参考：

- [poi 漏洞修复引发的一些问题.docx](./poi 漏洞修复引发的一些问题.docx)



解决思路：

- [jxls-1.0.6/src/jxls-core](./jxls-1.0.6/src/jxls-core)



修改`jxls-1.0.6/src/jxls-core/pom.xml`，把 poi依赖从3.9升级到4.1.2，此时，打包编译时，会报一些错，哪里报错改哪了就行了。

```
        <!-- jxls 1.0.6 适配 poi 4.1.2 -->
        <dependency>
            <groupId>org.apache.poi</groupId>
            <artifactId>poi</artifactId>
            <!--<version>3.9</version>-->
            <version>4.1.2</version>
        </dependency>
        <dependency>
            <groupId>org.apache.poi</groupId>
            <artifactId>poi-ooxml</artifactId>
            <!--<version>3.9</version>-->
            <version>4.1.2</version>
        </dependency>
```

注：由于我已经改造过了，直接获取代码拉取就行了



执行命令：

```
mvn clean install
```




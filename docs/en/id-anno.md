> The primary key annotation @TableId  function is the same as[ Mybatis-Plus](https://github.com/baomidou/mybatis-plus)(Hereafter referred to as MP), but compared to MP, some low-frequency usage functions have been castrated. According to user feedback, it can be added gradually with the iteration. The current version currently only supports the following two scenarios: 
> 
> 1. Rename the unique id in es
> 1. Specify the unique id generation method in es

Example:
```java
public class Document {
	/**
     * unique id in es
     */
    @TableId(value = "myId",type = IdType.AUTO)
    private String id;
    
    //  Omit other fields...
}
```
> **Tips:**
> - Since es has processed the default name of id (underscore + id): _id, EE has blocked this operation for you, you don't need to specify it in the annotation, and the framework will automatically complete the mapping for you.
> - Id generation types currently only support three types:
>    1. **IdType.AUTO:** It is automatically generated by ES and is the default configuration, no additional configuration is required for you. Recommended
>    1. **IdType.UUID:** The system generates UUID, and then inserts ES (not recommended)
>    1. **IdType.CUSTOMIZE:** (version number >= 0.9.6 support) is defined by the user, the user sets the id value by himself, if the id specified by the user does not exist in es, a new record will be added when inserting, if If the user-specified id already has a record in es, the record corresponding to the id will be updated automatically.
> - **Priority:** Annotation configured Id generation strategy>Globally configured Id generation strategy


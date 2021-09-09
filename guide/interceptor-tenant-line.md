# 多租户

## TenantLineInnerInterceptor

示例工程：

👉 [mybatis-plus-sample-tenant](https://gitee.com/baomidou/mybatis-plus-samples/tree/master/mybatis-plus-sample-tenant)

### 属性介绍

| 属性名 | 类型 | 默认值 | 描述 |
| :-: | :-: | :-: | :-: |
| tenantLineHandler | TenantLineHandler |  | 租户处理器（ TenantId 行级 ） |

```java
public interface TenantLineHandler {

    /**
     * 获取租户 ID 值表达式，只支持单个 ID 值
     * <p>
     *
     * @return 租户 ID 值表达式
     */
    Expression getTenantId();

    /**
     * 获取租户字段名
     * <p>
     * 默认字段名叫: tenant_id
     *
     * @return 租户字段名
     */
    default String getTenantIdColumn() {
        return "tenant_id";
    }

    /**
     * 根据表名判断是否忽略拼接多租户条件
     * <p>
     * 默认都要进行解析并拼接多租户条件
     *
     * @param tableName 表名
     * @return 是否忽略, true:表示忽略，false:需要解析并拼接多租户条件
     */
    default boolean ignoreTable(String tableName) {
        return false;
    }
}
```


# PlantUML Diagram Fixes Applied

## Summary
Fixed the PlantUML deployment architecture diagram to use the correct AWS icon paths and macro names from this repository (aws-icons-for-plantuml v20.0).

## Changes Made

### 1. Version Path Update
**Original:**
```plantuml
!define AWSPuml https://raw.githubusercontent.com/awslabs/aws-icons-for-plantuml/v2.0/dist
```

**Fixed:**
```plantuml
!define AWSPuml https://raw.githubusercontent.com/awslabs/aws-icons-for-plantuml/v20.0/dist
```

**Reason:** The repository is at version v20.0, not v2.0.

### 2. IAM Icon Include Path
**Original:**
```plantuml
!include AWSPuml/SecurityIdentityCompliance/IAM.puml
```

**Fixed:**
```plantuml
!include AWSPuml/SecurityIdentityCompliance/IdentityAccessManagementRole.puml
```

**Reason:** There is no `IAM.puml` file in the repository. The correct file for IAM roles is `IdentityAccessManagementRole.puml`.

### 3. IAM Macro Usage
**Original:**
```plantuml
IAMRole(iam_role, "IAM Role", "Temporary Credentials", $AWS_COLOR_NEBULA)
```

**Fixed:**
```plantuml
IdentityAccessManagementRole(iam_role, "IAM Role", "Temporary Credentials")
```

**Reason:**
- The macro name is `IdentityAccessManagementRole`, not `IAMRole`
- The standard macro accepts 3 parameters (alias, label, techn) or 4 parameters (alias, label, techn, descr)
- Colors are predefined in the macro definitions and cannot be overridden as a parameter

### 4. Other Service Macros
**CodeBuild macro:**
```plantuml
CodeBuild(build_runner, "CI/CD Runner", "Execute Steps")
```
- Removed the 4th parameter `$AWS_COLOR_NEBULA` as it's not supported

**ElasticContainerRegistry macro:**
```plantuml
ElasticContainerRegistry(ecr, "Amazon ECR", "Image Registry")
```
- Removed the 4th parameter `$AWS_COLOR_SMILE` as it's not supported

**CloudWatch macro:**
```plantuml
CloudWatch(cloudwatch, "CloudWatch", "Logs & Metrics")
```
- Removed the 4th parameter `$AWS_COLOR_COSMOS` as it's not supported

**ElasticKubernetesService macro:**
```plantuml
ElasticKubernetesService(eks_cluster, "IV. Amazon EKS Cluster", "campus-events-dev (K8s 1.31)")
```
- Removed the 4th parameter `$AWS_COLOR_SMILE` as it's not supported

## Available Files in Repository

### Containers
- `ElasticKubernetesService.puml` ✓
- `ElasticContainerRegistry.puml` ✓

### DeveloperTools
- `CodeBuild.puml` ✓

### ManagementGovernance
- `CloudWatch.puml` ✓

### SecurityIdentityCompliance
- `IdentityandAccessManagement.puml` - Main IAM service
- `IdentityAccessManagementRole.puml` - IAM Role icon ✓
- `IdentityAccessManagementAWSSTS.puml` - AWS STS
- Other IAM-related icons

## Macro Signature Reference

All AWS service macros follow these standard signatures:

**3 Parameters:**
```plantuml
ServiceName(e_alias, e_label, e_techn)
```

**4 Parameters:**
```plantuml
ServiceName(e_alias, e_label, e_techn, e_descr)
```

Where:
- `e_alias`: The unique identifier for the element
- `e_label`: The display label
- `e_techn`: Technology or subtitle text
- `e_descr`: (Optional) Additional description

Colors are predefined in each service's PUML file and cannot be customized via macro parameters.

## Files Created

1. `deployment-architecture-fixed.puml` - The corrected PlantUML diagram
2. `FIXES_APPLIED.md` - This documentation file

## Testing

To test the fixed diagram, you can:

1. Copy the contents of `deployment-architecture-fixed.puml`
2. Paste it into [PlantUML Online Editor](http://www.plantuml.com/plantuml/uml/)
3. Or use a local PlantUML renderer

## References

- Repository: https://github.com/awslabs/aws-icons-for-plantuml
- Version: v20.0
- README: https://github.com/awslabs/aws-icons-for-plantuml/blob/main/README.md

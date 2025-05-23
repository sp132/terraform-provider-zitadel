---
page_title: "zitadel_human_user Resource - terraform-provider-zitadel"
subcategory: ""
description: |-
  Resource representing a human user situated under an organization, which then can be authorized through memberships or direct grants on other resources.
---

# zitadel_human_user (Resource)

**Caution: Email can only be set verified if a password is set for the user, either with initial_password or during runtime**

Resource representing a human user situated under an organization, which then can be authorized through memberships or direct grants on other resources.

## Example Usage

```terraform
resource "zitadel_human_user" "default" {
  org_id                       = data.zitadel_org.default.id
  user_name                    = "humanfull@localhost.com"
  first_name                   = "firstname"
  last_name                    = "lastname"
  nick_name                    = "nickname"
  display_name                 = "displayname"
  preferred_language           = "de"
  gender                       = "GENDER_MALE"
  phone                        = "+41799999999"
  is_phone_verified            = true
  email                        = "test@zitadel.com"
  is_email_verified            = true
  initial_password             = "Password1!"
  initial_skip_password_change = true
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `email` (String) Email of the user
- `first_name` (String) First name of the user
- `last_name` (String) Last name of the user
- `user_name` (String) Username

### Optional

- `display_name` (String) Display name of the user
- `gender` (String) Gender of the user, supported values: GENDER_UNSPECIFIED, GENDER_FEMALE, GENDER_MALE, GENDER_DIVERSE
- `initial_hashed_password` (String, Sensitive) Initial hashed password for the user, not changeable after creation. Being able to pass an initial hashed password is useful in migration scenarios.
- `initial_password` (String, Sensitive) Initially set password for the user, not changeable after creation
- `initial_skip_password_change` (Boolean) Whether the user has to change the password on first login.
- `is_email_verified` (Boolean) Is the email verified of the user, can only be true if password of the user is set
- `is_phone_verified` (Boolean) Is the phone verified of the user
- `nick_name` (String) Nick name of the user
- `org_id` (String) ID of the organization
- `phone` (String) Phone of the user
- `preferred_language` (String) Preferred language of the user

### Read-Only

- `id` (String) The ID of this resource.
- `login_names` (List of String) Loginnames
- `preferred_login_name` (String) Preferred login name
- `state` (String) State of the user

## Import

```bash
# The resource can be imported using the ID format `id[:org_id][:initial_password]>`, e.g.
terraform import zitadel_human_user.imported '123456789012345678:123456789012345678:Password1!'
```

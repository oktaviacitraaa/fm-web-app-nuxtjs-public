<template>
  <v-container class="fill-height ma-0" fluid>
    <v-row justify="center">
      <v-col cols="12" sm="10" md="8" lg="5">
        <v-card ref="form" class="pa-md-4 mx-lg-auto">
          <v-card-title>Sign In</v-card-title>
          <v-card-text>
            <v-text-field
              ref="email"
              v-model="email"
              :rules="[() => !!email || 'This field is required']"
              :error-messages="errorMessages"
              label="Email"
              placeholder="example123@moneyking.com"
              required
            />
            <v-text-field
              v-model="password"
              :append-icon="show1 ? 'mdi-eye-off' : 'mdi-eye'"
              :rules="[rules.required, rules.min]"
              :type="show1 ? 'text' : 'password'"
              name="input-10-1"
              label="Password"
              hint="At least 8 characters"
              counter
              @click:append="show1 = !show1"
            />
            <span>Forget your account? <a href="#" color="primary"> Remember it! </a></span>
          </v-card-text>
          <v-card-actions>
            <v-btn block large text class="primary text-none" to="/feature/dashboard/">
              SIGN IN
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  layout: 'empty',
  head () {
    return {
      title: 'Sign In'
    }
  },
  data () {
    return {
      show1: false,
      password: 'Password',
      rules: {
        required: value => !!value || 'Required.',
        min: v => v.length >= 8 || 'Min 8 characters',
        emailMatch: () => ('The email and password you entered don\'t match')
      }
    }
  }
}
</script>

<template>
  <section class="container">
    <h1>Formulario de Angular </h1><br><br>
    <form @submit.prevent="agregarPersona">
      <section>
        <label>Nombre:</label><br>
        <input name="nombre" type="string" v-model="form.nombre" required>
      </section><br>
      <section>
        <label>Apellido:</label><br>
        <input name="apellido" type="string" v-model="form.apellido" required>
      </section><br>
      <section>
        <label>Edad:</label><br>
        <input name="edad" type="number" min="1" max="120" step="1" v-model="form.edad" required>
      </section><br>
      <section>
        <label>Cédula:</label><br>
        <input name="cedula" type="number" v-model="form.cedula" required>
      </section><br>
      <button type="submit">Guardar</button>
    </form>
  </section>

  <section class="container">
    <table>
      <tr v-for="item in personas" :key="item.id">
        <td>{{ item.nombre }} {{ item.apellido }} tiene: {{ item.edad }} años y su cédula es: {{ item.cedula }}</td>
        <td v-if="item.edad >= 18">Es mayor de edad</td>
        <td v-if="item.edad < 18">Es menor de edad</td>
      </tr>
    </table>
  </section>
</template>

<script>
export default {
  data() {
    return {
      personas: [],
      form: {
        nombre: '',
        apellido: '',
        edad: '',
        cedula: ''
      }
    };
  },
  methods: {
    agregarPersona() {
      this.personas.push({
        nombre: this.form.nombre,
        apellido: this.form.apellido,
        edad: this.form.edad,
        cedula: this.form.cedula
      });

      this.form = {
        nombre: '',
        apellido: '',
        edad: '',
        cedula: ''
      };

      // console.log(this.personas);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 550px;
  border: 1px solid rgb(29, 63, 22);
  background-color: rgb(228, 255, 225);
}

form {
  margin: 10px;
  align-items: center;
  justify-content: left;
}

table {
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
  border: 1px solid #000;
}

th,
td {
  border: 1px solid #000;
}

input {
  width: 240px;
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
}

h1 {
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
  margin: 5px;
}

label {
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
  font-weight: 900;
}

button {
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
  font-weight: 700;
  padding: 10px;
  margin: 10px;
  display: flex;
  cursor: pointer;
  border: 1px solid black;
  font-size: 15px;
  background-color: rgb(134, 175, 123);
}
</style>
